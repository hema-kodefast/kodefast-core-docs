# Quick Deployment Checklist

## Pre-Deployment Preparation

### 1. Prerequisites Setup

- [ ] Node.js v16+ installed on client server
- [ ] Git access configured
- [ ] MinIO server access/installation permissions
- [ ] Backup access to existing deployment

### 2. Repository and Dependencies

```bash
# Step 1: Clone and Setup KV Repository
git clone https://gitlab.com/prudhvi99/kv.kodefast.net.git
cd kv.kodefast.net
npm install
```

### 3. Environment Configuration

Create `.env` file with:

```bash
# Server Configuration
PORT=3000
API_VERSION=v1.0
NODE_ENV=production

# Admin Credentials
ADMIN_USERNAME="kfadmin"
ADMIN_PASSWORD="kf@2025*"

# API Authentication
API_KEY=""

# AWS S3 Configuration (for migration)
AWS_REGION="us-east-1"
S3_BUCKET="assets.kodefast.net"
AWS_ACCESS_KEY_ID=""
AWS_SECRET_ACCESS_KEY=""

# Database Configuration
DATABASE_PATH=./kodefast.db

# MinIO Configuration (client server)
MINIO_ENDPOINT=your-client-minio-endpoint
MINIO_ACCESS_KEY=your-client-minio-access-key
MINIO_SECRET_KEY=your-client-minio-secret-key
MINIO_BUCKET_NAME=icons-bucket
```

## Deployment Steps

### Step 1: Deploy KV Storage

- [ ] Clone kv.kodefast.net repository
- [ ] Run `npm install`
- [ ] Configure environment variables
- [ ] Deploy application (`npm start` or PM2)
- [ ] Verify API health: `curl -H "Authorization: xxxxxxx" http://localhost:3000/health`

### Step 2: Database Migration

- [ ] Backup existing database: `cp kodefast.db kodefast.db.backup`
- [ ] Transfer database to new server
- [ ] Verify database integrity: `sqlite3 kodefast.db "PRAGMA integrity_check;"`
- [ ] Set proper permissions: `chmod 644 kodefast.db`

### Step 3: MinIO Setup and S3 Migration

- [ ] Install and configure MinIO server
- [ ] Create icons bucket: `mc mb myminio/icons-bucket`
- [ ] Set public read policy: `mc policy set public myminio/icons-bucket`
- [ ] Migrate icons from S3:
  ```bash
  aws s3 sync s3://assets.kodefast.net/icons/ ./temp-icons/
  mc cp --recursive ./temp-icons/ myminio/icons-bucket/
  ```
- [ ] Verify migration: `mc ls myminio/icons-bucket/`

### Step 4: Frontend Configuration

- [ ] Update environment variables:
  ```bash
  VUE_APP_KV_API_BASE_URL=https://kv.kodefast.net
  VUE_APP_KV_API_AUTH_KEY=xxxxx
  VUE_APP_ASSETS_S3_BASE_URL=https://your-minio-server.com:9000/icons-bucket
  ```
- [ ] Rebuild frontend: `npm run build`
- [ ] Deploy updated frontend

## Post-Deployment Verification

### API Testing

- [ ] Test KV API: `curl -H "Authorization: xxxxx" https://kv.kodefast.net/company-icons/test`
- [ ] Test MinIO access: `curl https://minio-server.com:9000/icons-bucket/dashboard.svg`

### Frontend Testing

- [ ] Open application and navigate to icon interface
- [ ] Verify icons load correctly
- [ ] Test icon search functionality
- [ ] Test new icon uploads

### Performance Check

- [ ] Monitor API response times
- [ ] Check server resource usage
- [ ] Verify database performance

## Environment Variables Summary

### KV Server Environment

```bash
PORT=3000
API_VERSION=v1.0
ADMIN_USERNAME="kfadmin"
ADMIN_PASSWORD="kf@2025*"
API_KEY="xxxxxxx"
AWS_REGION="us-east-1"
S3_BUCKET="assets.kodefast.net"
AWS_ACCESS_KEY_ID=""
AWS_SECRET_ACCESS_KEY=""
DATABASE_PATH=./kodefast.db
MINIO_ENDPOINT=your-client-minio-endpoint
MINIO_ACCESS_KEY=your-client-minio-access-key
MINIO_SECRET_KEY=your-client-minio-secret-key
MINIO_BUCKET_NAME=icons-bucket
```

### Frontend Environment

```bash
VUE_APP_KV_API_BASE_URL=https://kv.kodefast.net
VUE_APP_KV_API_AUTH_KEY=xxxxxxx
VUE_APP_ASSETS_S3_BASE_URL=https://your-minio-server.com:9000/icons-bucket
```

## Critical Integration Points

The following files in your codebase automatically use these environment variables:

1. **`src/config/app.js`** (lines 133-135):

   - `kvKodefastUrl`: KV API endpoint
   - `authKey`: API authentication key
   - `s3BaseUrl`: MinIO/S3 base URL for icons

2. **`src/repo/iconsRepo.js`**:

   - `fetchAllIconsFromKodefastAPI()`: Uses `kvKodefastUrl`
   - `fetchSvgContentFromS3()`: Uses `s3BaseUrl`
   - `createIcons()`, `getIcons()`: Use authentication

3. **Icon Components**:
   - `src/layouts/IconsV2.vue`
   - `src/layouts/IconsList.vue`
   - `src/layouts/Icons.vue`

## Troubleshooting Quick Fixes

### Database Issues

```bash
# Check permissions
ls -la kodefast.db
# Fix permissions
chmod 644 kodefast.db
```

### MinIO Issues

```bash
# Check service
systemctl status minio
# Test connectivity
mc admin info myminio
```

### API Issues

```bash
# Test health endpoint
curl -H "Authorization: xxxxxxx" https://kv.kodefast.net/health
# Check logs
pm2 logs kv-api
```

### Frontend Issues

```bash
# Check environment variables
echo $VUE_APP_KV_API_BASE_URL
# Test direct icon access
curl https://minio-server.com:9000/icons-bucket/test-icon.svg
```

## Success Criteria

Deployment is successful when:

- [ ] KV API responds to health checks
- [ ] Database queries execute successfully
- [ ] MinIO serves icon files
- [ ] Frontend loads icons without errors
- [ ] Icon search and upload functions work
- [ ] Performance meets expectations

---
