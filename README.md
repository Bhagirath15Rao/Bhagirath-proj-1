# Project - Containerized Web Application with Kubernetes (EKS) and Docker

## Project Overview

This project demonstrates the process of building, hosting, and deploying a containerized web application using Kubernetes (Amazon EKS) and Docker. The application is enhanced to load a configurable background image from an S3 bucket, interact with a MySQL database, and incorporate secure handling of sensitive data using Kubernetes secrets.

### Key Features:
- **Flask Web Application**: The application is built using Flask and serves an HTML page. It displays a configurable background image retrieved from a private Amazon S3 bucket.
- **Database Integration**: MySQL is used as the backend database, with the credentials passed securely to the application through Kubernetes secrets.
- **Dockerization**: The application is containerized using Docker, and the Docker image is automatically built, tested, and published to Amazon ECR via GitHub Actions.
- **Persistent Storage**: MySQL data is stored using Amazon EBS persistent volumes, ensuring data durability.
- **Kubernetes (EKS)**: The application is deployed to an Amazon EKS cluster with 2 worker nodes, using Kubernetes manifests to create resources such as ConfigMaps, Secrets, PersistentVolumeClaims, Deployments, and Services.
- **IAM Roles**: IAM Roles for Service Accounts (IRSA) are used to grant the application access to the private S3 bucket.
- **Auto-scaling **: Horizontal Pod Autoscaling (HPA) is implemented to automatically scale the application based on traffic load.

### Steps Taken:
1. **Enhancement of Flask Application**:
   - Configurable background image loaded from S3.
   - Logs URL of the background image.
   - Added environment variable for the header name via ConfigMap.
   - Database credentials passed securely via Kubernetes secrets.

2. **Docker Image Creation**:
   - Created a Dockerfile and built the Docker image locally in Cloud9.
   - Automated the build process using GitHub Actions to push the image to Amazon ECR.

3. **Kubernetes Deployment**:
   - Created a namespace `final` and deployed MySQL and Flask applications to Amazon EKS.
   - Configured Kubernetes manifests for ConfigMap, Secret, PersistentVolumeClaim, and Deployments for MySQL and Flask apps.
   - Exposed MySQL and Flask apps using Kubernetes services.

4. **S3 Integration**:
   - Stored the background image in a private S3 bucket.
   - Configured a service account with permissions to access the S3 bucket via IRSA.

5. **Scaling and Automation **:
   - Implemented Horizontal Pod Autoscaling (HPA) based on traffic load.
   - Automated deployments using Flux (Bonus feature).

6. **Application Updates**:
   - Demonstrated dynamic updates by replacing the background image in S3 and updating the ConfigMap to reflect the new image in the browser.

---

## Tools and Services Used:
- **GitHub**: For storing the application code and Kubernetes manifests.
- **GitHub Actions**: For automating Docker image build and deployment to Amazon ECR.
- **Docker**: For containerizing the application and building the image.
- **Amazon ECR**: To securely store Docker images.
- **Amazon EKS**: To deploy and manage the application in a scalable Kubernetes cluster.
- **Amazon S3**: For storing background images.
- **Amazon EBS**: For persistent storage of MySQL data.
- **kubectl**: For interacting with the Kubernetes cluster.
- **eksctl**: For creating and managing the EKS cluster.
- **IAM Roles**: For secure access to AWS resources.

---
