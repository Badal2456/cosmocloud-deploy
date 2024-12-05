# Cosmocloud Deployment Helm Chart

This Helm chart deploys three components of the Cosmocloud application:
- Backend
- Frontend
- Redis Database

## Features
- **Backend**:
  - Image: `shreybatra/sample-backend`
  - Service Type: `ClusterIP`
  - Port: `8000`
  - Environment Variable: `REDIS_URI=redis://redis-svc:6379`
- **Frontend**:
  - Image: `shreybatra/sample-frontend`
  - Service Type: `NodePort`
  - Port: `5173` (exposed on NodePort `31000`)
  - Environment Variable: `BACKEND_URL=http://backend-svc:8000`
- **Redis**:
  - Image: `redis`
  - Service Type: `ClusterIP`
  - Port: `6379`

## How to Deploy
1. Install the Helm chart:
   ```bash
   helm install testapp cosmocloud-deploy --atomic --timeout 30s
