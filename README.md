
#First build the project
mvn clean install

# Build 'backend' image.
docker build -t backend:latest .

# To run 'backend' image.
docker run -p 8888:8080 backend:latest -it

Backend API url : http://localhost:8888/name


# Start minikube
minikube start

# Set docker env
eval $(minikube docker-env)             # unix shells
minikube docker-env | Invoke-Expression # PowerShell

# Deploy in minikube
kubectl apply -f Kubernetes/deployment.yaml

# Check that it's running
kubectl get pods


#Deploy using helm
helm install backend backend-chart/ --values backend-chart/values.yaml