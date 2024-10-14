# depi-project

The depi-project automates the build, test, and deployment process for a Dockerized Flask application using Jenkins CI/CD, Docker, Kubernetes, and Ansible. The project is deployed on AWS Elastic Kubernetes Service (EKS) and uses Terraform to provision cloud resources.

## Key Technologies

- **Flask**: Web application framework.
- **Docker**: For containerizing the Flask application.
- **Kubernetes**: Orchestration platform, using AWS EKS.
- **Terraform**: Infrastructure as Code (IaC) to provision AWS resources.
- **Jenkins**: Automating the CI/CD pipeline.
- **GitHub**: Version control for source code.
- **Docker Hub**: Container image repository.
- **Slack**: For notifications on pipeline status.

## Project Setup

### 1. GitHub Repository

The project code is hosted on a GitHub repository and includes:

- `app.py`: The Flask application.
- `requirements.txt`: Python dependencies.
- `Dockerfile`: Instructions to build the Docker image.
- Kubernetes YAML files: Includes deployment and service configuration.
- Jenkinsfile: Defines the CI/CD pipeline.

### 2. Docker Repository

The Dockerized Flask app is stored in the Docker Hub repository:  
`mohamed907/depi-flask-app`

### 3. AWS EKS Setup

Using **Terraform**, an EKS cluster with 3 worker nodes was created. An EC2 instance was provisioned to run Jenkins as the CI/CD controller node.

## Infrastructure Setup

### AWS Resources

- **EKS Cluster**: 3-node cluster for high availability.
- **EC2 Instance**: Jenkins CI/CD controller.

### Terraform Files

Terraform is used to automate the creation of the AWS infrastructure. Ensure relevant Terraform files are included in the repository.

## Jenkins Pipeline

### Pipeline Stages

1. **Clone Repository**: Pulls the latest code from GitHub.
2. **Build Docker Image**: Builds the Flask app into a Docker image.
3. **Push Docker Image**: Pushes the image to Docker Hub.
4. **Deploy to EKS**: Uses `kubectl` to deploy the app to the EKS cluster.

### Slack Integration

Slack notifications are sent for successful or failed builds. Ensure Slack is configured with your workspace and the Jenkins Slack plugin is installed.

## Deployment Process

### Dockerization

The Flask app is Dockerized using a multi-step build that installs the dependencies and copies the app into the container.

### Kubernetes Deployment

The application is deployed to EKS using Kubernetes deployment and service YAML files that define the app's configuration and expose it externally via a LoadBalancer.

## Testing and Validation

### Webhook Testing

After setting up the GitHub webhook, the pipeline was tested by modifying the Flask app. Each commit successfully triggered the pipeline.

### Automated Deployment

Each successful pipeline build pushes a new Docker image to Docker Hub and redeploys the app to the EKS cluster.

## Monitoring and Scaling

- **Kubernetes** provides auto-scaling based on demand, ensuring high availability.
- **Terraform** manages the scaling of the EKS cluster.

## Project Completion

This project demonstrates a fully automated CI/CD pipeline from code commit to deployment on AWS EKS using Jenkins, Docker, and Kubernetes.

## How to Contribute

Feel free to submit pull requests to improve the project, add new features, or fix bugs.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
