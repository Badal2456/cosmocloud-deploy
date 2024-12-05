# Helm Chart for Cosmocloud Deploy

## Project Overview
This project involves creating a Helm chart to deploy a backend, frontend, and Redis DB on AWS EKS. The services are deployed as Deployments with 1 replica each, and the necessary environment variables are passed during deployment.

## Challenges Faced
### 1. EKS Cluster Creation
Initially, I faced challenges connecting to the EKS cluster due to IAM role and RBAC misconfigurations. I was unable to list the nodes and access the cluster, which led me to troubleshoot using CloudWatch logs and other debugging steps.

### 2. Troubleshooting
The error I faced was related to authentication, where I couldn’t connect to the cluster. After reviewing my IAM roles and permissions, I corrected the configuration and ensured the correct RBAC settings.

### 3. Connection Issues
Due to certain limitations in accessing the cluster directly, I focused on creating the Helm charts and ensuring they would be deployable once the EKS cluster connection is stable.

## Steps Taken to Complete the Task
### 1. Helm Chart Creation
I created the folder structure for the Helm chart `cosmocloud-deploy` which includes the following files:
- **Chart.yaml**: Contains metadata for the Helm chart.
- **values.yaml**: Specifies environment variables and configuration settings for each service.
- **templates/deployment.yaml**: Defines Kubernetes Deployment resources for backend, frontend, and Redis services.
- **templates/service.yaml**: Defines the Kubernetes Service resources for each application.

### 2. Service and Deployment Setup
- **Backend**: The backend service was set up to use the image `shreybatra/sample-backend` with the environment variable `REDIS_URI=redis://redis-svc:6379`.
- **Frontend**: The frontend service used the image `shreybatra/sample-frontend` with the environment variable `BACKEND_URL=http://backend-svc:8000`.
- **Redis**: The Redis service used the official Redis image, and it was configured with the necessary port and service type.

### 3. Helm Commands Used
- `helm install testapp cosmocloud-deploy --atomic --timeout 30s`: This command installs the Helm chart to deploy the application services.

## Conclusion
Despite some initial difficulties connecting to the EKS cluster, I was able to complete the Helm chart for deploying the backend, frontend, and Redis services. The Helm chart is now ready for use, and the services are configured to work together seamlessly.

## Future Work
Once the connection to the EKS cluster is fully established, the Helm chart can be deployed successfully to the Kubernetes environment.
