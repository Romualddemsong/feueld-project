[this is the docker repository where](https://hub.docker.com/repository/docker/romualddemsong/feueld_ass/general)


[This is a graphical observation of the infrastructure deployed on aws](https://drive.google.com/file/d/1KCLVMiKkhPUGHChd4vvGLFM9c0XDqxBR/view?usp=drive_link)

# feueld-project

Interview assessment
- Setting up Infrastructure with Terraform on AWS (EKS):
- Provision necessary infrastructure components such as VPC, subnets, security groups, and EKS cluster using Terraform.
- Ensure proper isolation of resources for different environments (development, staging, production).
- Containerizing Applications with Docker:
- Dockerize both frontend and backend applications to ensure portability and consistency across environments.
- Optimize Dockerfiles for security and efficiency.
- Deploying Applications on Kubernetes (EKS):
- Define Kubernetes manifests (Deployment, Service, Ingress) for frontend and backend applications.
- Utilize Horizontal Pod Autoscaler (HPA) for auto-scaling based on CPU utilization.
- Implement readiness and liveness probes for auto-healing capabilities.
- Ensure proper network policies to restrict access to backend services.
- Implementing Monitoring and Observability:
	- Integrate monitoring tools such as Prometheus and Grafana for cluster monitoring.
	- Utilize Kubernetes-native monitoring features for application-level metrics.
	- Configure logging with tools like Fluentd and Elasticsearch for capturing application logs.
	- Expose metrics and logs for monitoring and troubleshooting purposes
# Download helm
-
- ``curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3``
- ``chmod 700 get_helm.sh``
- ``./get_helm.sh``
- ``helm version``


# Install prometheus Grafana
- ``helm repo add stable https://charts.helm.sh/stable``
- ``helm repo add prometheus-community https://prometheus-community.github.io/helm-charts``
- ``helm search repo prometheus-community``
- ``helm install stable prometheus-community/kube-prometheus-stack``
- ``kubectl edit svc stable-kube-prometheus-sta-prometheus       // use LoadBalancer``
- ``kubectl edit svc stable-grafana       // use LoadBalancer``


*UserName: admin* 
*Password: prom-operator*


**Recall**
- docker composed file have syntax and a missing port binding
- Took some personnal decision on decidion on the availability, scalability and fault tolerant aspect of the infrastructure
- The terraform state will be store in the default local but a remote backend can be add in the each environment at the time of execution and base on the requirements.
