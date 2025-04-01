# AWS EKS Voting App Deployment

Welcome to the **AWS EKS Voting App Deployment** project! 🎉 This application demonstrates a full **CI/CD pipeline** for deploying a voting app using a **microservices architecture** on **AWS EKS**. The project leverages modern technologies such as **Kubernetes**, **Docker**, **GitHub Actions**, and **PostgreSQL** to offer a scalable, efficient, and cloud-native solution.

The voting app lets users cast their votes, and the results are dynamically displayed in real-time. The entire deployment process is automated with **GitHub Actions**, which handles the building, testing, and deployment of the app to the cloud.

---

## 🔧 Technologies Used

- **Frontend:** React.js (Web interface for the voting app)
- **Backend:** Node.js (Handles voting logic and database interaction)
- **Database:** PostgreSQL (Stores votes and results)
- **CI/CD:** GitHub Actions (Automated build and deployment pipeline)
- **Containerization:** Docker (For building, testing, and running containers)
- **Infrastructure:** AWS EKS (Elastic Kubernetes Service for cloud-native deployment)
- **Orchestration:** Kubernetes (Manages microservices in the cloud)

---

## 📋 Features

- **Microservices Architecture:** Each service (frontend, backend, result) runs in a separate container, making it scalable.
- **Real-time Voting:** Users can cast their votes, and the results are updated live.
- **Kubernetes Deployment:** The application is deployed on **AWS EKS**, using **Kubernetes** for container orchestration.
- **Automated CI/CD Pipeline:** **GitHub Actions** automates the building, testing, and deployment of Docker images to **AWS EKS**.
- **Stateless PostgreSQL:** Utilizes PostgreSQL in a stateless manner, enhancing scalability and fault tolerance by maintaining data storage without relying on local disk storage or maintaining state between sessions.
- **Versioning:** Each microservice has its own version number, simplifying the management of different versions.

---

## 🚀 GitHub Actions Pipeline

The project uses **GitHub Actions** to automate the entire pipeline:

- **Checkout Code:** Pull the latest code from GitHub.
- **Login to Docker:** Authenticate to Docker Hub or **Amazon ECR**.
- **Build Docker Images:** The pipeline builds Docker images for each microservice (result, vote, worker).
- **Configure AWS Credentials:** Set up the necessary AWS credentials for deployment.
- **Install and Configure kubectl:** Set up **kubectl** for Kubernetes interaction.
- **Generate Kubernetes Manifests:** Automatically generate Kubernetes deployment, service, and ingress files.
- **Deploy to EKS:** Deploy the app to **AWS EKS**.

The pipeline configuration is located in the `.github/workflows` folder.

### Example Workflow:

- Build Docker images and tag them with the latest version.
- Push images to Docker Hub or **Amazon ECR**.
- Deploy the app to **AWS EKS** using Kubernetes manifests.

---

## 🖋️ Versioning

**Semantic versioning** is used to manage the application's version:

Example: When you push a new tag (`git push v3.0.4`), the images will be tagged as:
- `pokfinner/result:3.0.4`
- `pokfinner/vote:3.0.4`
- `pokfinner/worker:3.0.4`

Each microservice has a version number, helping maintain compatibility across deployments.

---

## 📦 Deployment to AWS EKS

### Steps to deploy the app to AWS EKS:

1. **Ensure a running AWS EKS cluster.**
2. **Configure kubectl and AWS CLI** on your local machine.
3. **Push Docker images** to Docker Hub or Amazon ECR.
4. **Apply Kubernetes manifests:**
   ```bash
   kubectl apply -f k8s/manifests/*.yaml
