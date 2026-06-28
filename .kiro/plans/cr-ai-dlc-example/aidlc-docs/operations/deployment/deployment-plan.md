# Deployment Plan

## 1. Overview
Document này mô tả chi tiết quy trình triển khai hệ thống.

**Environment**: Development | Staging | Production  
**Deployment Type**: Initial Deployment | Update | Rollback  
**Scheduled Date**: [Date and Time]  
**Estimated Duration**: [X hours]

---

## 2. Pre-Deployment Checklist

### 2.1 Code Readiness
- [ ] All tests passing (unit, integration, e2e)
- [ ] Code review completed and approved
- [ ] Security scan passed (no critical vulnerabilities)
- [ ] Performance testing completed
- [ ] Documentation updated

### 2.2 Infrastructure Readiness
- [ ] Target environment is healthy
- [ ] Database backups completed
- [ ] Rollback plan prepared
- [ ] Monitoring and alerts configured
- [ ] Resource capacity verified

### 2.3 Team Readiness
- [ ] Deployment team notified
- [ ] On-call engineers available
- [ ] Stakeholders informed
- [ ] Communication channels ready

---

## 3. Deployment Strategy

### 3.1 Deployment Method
**Selected Strategy**: Blue-Green | Canary | Rolling | Recreate

**Rationale**: [Why this strategy was chosen]

### 3.2 Blue-Green Deployment (Example)
```
┌─────────────┐         ┌─────────────┐
│  Blue Env   │ ◄───────│   Router    │
│  (Current)  │         │             │
└─────────────┘         └─────────────┘
                              │
                              ▼
                        ┌─────────────┐
                        │  Green Env  │
                        │   (New)     │
                        └─────────────┘

Step 1: Deploy to Green
Step 2: Test Green
Step 3: Switch router to Green
Step 4: Keep Blue as backup
```

---

## 4. Deployment Steps

### Phase 1: Pre-Deployment (T-1 hour)
**Duration**: 30 minutes

1. **Verify Environment Health**
   ```bash
   # Check services status
   kubectl get pods -n production
   # Check database connectivity
   psql -h db.prod.com -U admin -c "SELECT 1"
   ```

2. **Create Backup**
   ```bash
   # Database backup
   pg_dump -h db.prod.com -U admin > backup_$(date +%Y%m%d_%H%M%S).sql
   # Application state backup
   kubectl get all -n production -o yaml > k8s_backup.yaml
   ```

3. **Notify Stakeholders**
   - Send deployment start notification
   - Update status page

**Rollback Point**: Can abort deployment, no changes made

---

### Phase 2: Deployment Execution (T0)
**Duration**: 45 minutes

#### Step 1: Database Migration (If Applicable)
**Duration**: 10 minutes

```bash
# Run database migrations
npm run migrate:prod
# Or
./scripts/run-migrations.sh production
```

**Verification**:
```bash
# Check migration status
npm run migrate:status
```

**Rollback Point**: If migrations fail, rollback using:
```bash
npm run migrate:rollback
```

---

#### Step 2: Deploy Backend Services
**Duration**: 20 minutes

**Option A: Kubernetes**
```bash
# Update image version
kubectl set image deployment/api-server api-server=myregistry/api:v1.2.3 -n production

# Watch rollout status
kubectl rollout status deployment/api-server -n production

# Verify deployment
kubectl get pods -n production
```

**Option B: Docker Compose**
```bash
# Pull new images
docker-compose -f docker-compose.prod.yml pull

# Deploy with zero downtime
docker-compose -f docker-compose.prod.yml up -d --no-deps --build api
```

**Option C: Traditional Server**
```bash
# SSH to server
ssh user@prod-server.com

# Pull latest code
cd /app && git pull origin main

# Install dependencies
npm ci --production

# Restart service
pm2 restart api-server
```

**Verification**:
```bash
# Health check
curl https://api.prod.com/health
# Expected: {"status": "ok", "version": "1.2.3"}
```

---

#### Step 3: Deploy Frontend
**Duration**: 10 minutes

```bash
# Build production bundle
npm run build

# Upload to CDN/S3
aws s3 sync ./dist s3://my-app-prod --delete

# Invalidate CloudFront cache
aws cloudfront create-invalidation --distribution-id EXXXXX --paths "/*"
```

**Verification**:
```bash
# Check version
curl https://app.prod.com/version.json
```

---

#### Step 4: Deploy Infrastructure Changes (If Applicable)
**Duration**: 5 minutes

```bash
# Apply Terraform changes
cd infrastructure/
terraform plan -out=tfplan
terraform apply tfplan

# Or Kubernetes configs
kubectl apply -f k8s/production/
```

---

### Phase 3: Post-Deployment Verification (T+45min)
**Duration**: 30 minutes

#### Step 1: Smoke Tests
```bash
# Run automated smoke tests
npm run test:smoke:prod

# Or manual checks
curl -X POST https://api.prod.com/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"test123"}'
```

**Critical Paths to Test**:
- [ ] User login
- [ ] Create transaction
- [ ] View dashboard
- [ ] API health endpoints

---

#### Step 2: Monitor Key Metrics
**Metrics to Watch** (first 30 minutes):
- Error rate: Should be < 1%
- Response time: Should be < 500ms p95
- CPU/Memory: Should be stable
- Database connections: Should not spike

**Monitoring Tools**:
```bash
# Check logs
kubectl logs -f deployment/api-server -n production

# Or
pm2 logs api-server --lines 100

# Check metrics dashboard
open https://grafana.prod.com/dashboard
```

---

#### Step 3: Gradual Traffic Shift (Canary)
If using canary deployment:

```bash
# Shift 10% traffic to new version
kubectl patch service api-service -p '{"spec":{"selector":{"version":"v1.2.3","weight":"10"}}}'

# Wait and monitor...

# Shift 50%
kubectl patch service api-service -p '{"spec":{"selector":{"weight":"50"}}}'

# Wait and monitor...

# Shift 100%
kubectl patch service api-service -p '{"spec":{"selector":{"weight":"100"}}}'
```

---

### Phase 4: Finalization (T+1h15min)
**Duration**: 15 minutes

1. **Update Documentation**
   - [ ] Update CHANGELOG.md
   - [ ] Update deployment history
   - [ ] Document any issues encountered

2. **Notify Stakeholders**
   - Send deployment success notification
   - Update status page to "Operational"

3. **Archive Deployment Artifacts**
   ```bash
   # Tag release
   git tag -a v1.2.3 -m "Production release v1.2.3"
   git push origin v1.2.3
   
   # Archive deployment logs
   kubectl logs deployment/api-server > deployment_logs_v1.2.3.txt
   ```

---

## 5. Rollback Procedures

### 5.1 When to Rollback
Trigger rollback if:
- Error rate > 5% for 5 minutes
- Critical functionality broken
- Data corruption detected
- Performance degradation > 50%

### 5.2 Rollback Steps

#### Quick Rollback (< 5 minutes)
```bash
# Kubernetes
kubectl rollout undo deployment/api-server -n production

# Docker Compose
docker-compose -f docker-compose.prod.yml up -d --no-deps api:v1.2.2

# PM2
pm2 deploy production revert 1
```

#### Full Rollback (15-30 minutes)
1. **Rollback Application**
   ```bash
   # Revert to previous version
   kubectl set image deployment/api-server api-server=myregistry/api:v1.2.2
   ```

2. **Rollback Database (If Needed)**
   ```bash
   # Restore from backup
   psql -h db.prod.com -U admin < backup_20240615_080000.sql
   ```

3. **Verify Rollback**
   ```bash
   # Check version
   curl https://api.prod.com/health
   # Expected: {"version": "1.2.2"}
   ```

4. **Notify Team**
   - Alert stakeholders about rollback
   - Create incident report

---

## 6. Monitoring & Alerts

### 6.1 Key Metrics Dashboard
**URL**: https://grafana.prod.com/deployment

**Metrics to Monitor**:
- Request rate (req/sec)
- Error rate (%)
- Response time (p50, p95, p99)
- CPU usage (%)
- Memory usage (%)
- Database query time (ms)

### 6.2 Alert Configuration
```yaml
# Example Prometheus alert
- alert: HighErrorRate
  expr: rate(http_requests_total{status="5xx"}[5m]) > 0.05
  for: 5m
  labels:
    severity: critical
  annotations:
    summary: "High error rate detected"
    description: "Error rate is {{ $value }} req/sec"
```

---

## 7. Communication Plan

### 7.1 Notification Templates

**Deployment Start**:
```
🚀 Deployment Started: v1.2.3
Environment: Production
Estimated Duration: 1.5 hours
Expected Completion: [Time]
Status: https://status.company.com
```

**Deployment Success**:
```
✅ Deployment Completed: v1.2.3
Environment: Production
Duration: 1.2 hours
Changes: [Link to release notes]
```

**Deployment Issues**:
```
⚠️  Deployment Issue: v1.2.3
Issue: [Description]
Impact: [User impact]
Action: [Investigating/Rollback in progress]
ETA: [Time]
```

### 7.2 Communication Channels
- Slack: #deployments
- Email: engineering@company.com
- Status Page: https://status.company.com

---

## 8. Environment-Specific Configurations

### 8.1 Development
- **URL**: https://dev.company.com
- **Auto-deploy**: On merge to `develop` branch
- **Database**: dev-db.company.com

### 8.2 Staging
- **URL**: https://staging.company.com
- **Deploy trigger**: Manual or on tag `staging-*`
- **Database**: staging-db.company.com (production clone)

### 8.3 Production
- **URL**: https://app.company.com
- **Deploy trigger**: Manual only, on tag `v*`
- **Database**: prod-db.company.com

---

## 9. Post-Deployment Review

### 9.1 Deployment Retrospective
**Schedule**: Within 24 hours after deployment

**Topics**:
- What went well?
- What went wrong?
- What can be improved?
- Action items

### 9.2 Deployment Metrics
| Metric | Target | Actual |
|--------|--------|--------|
| Deployment duration | 1.5h | [Actual] |
| Downtime | 0 min | [Actual] |
| Rollback count | 0 | [Actual] |
| Issues found | 0 | [Actual] |

---

## 10. Appendix

### 10.1 Useful Commands
```bash
# View logs
kubectl logs -f deployment/api-server --tail=100

# Restart service
kubectl rollout restart deployment/api-server

# Scale service
kubectl scale deployment/api-server --replicas=5

# Check resource usage
kubectl top pods -n production
```

### 10.2 Emergency Contacts
| Role | Name | Phone | Slack |
|------|------|-------|-------|
| Tech Lead | [Name] | [Phone] | @handle |
| DevOps | [Name] | [Phone] | @handle |
| On-call | [Name] | [Phone] | @handle |

---

## Change Log
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | DevOps Team | Initial plan |
| 1.1 | [Date] | [Name] | Added canary steps |
