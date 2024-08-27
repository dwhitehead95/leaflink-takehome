# LeafLink Take Home

Install dependencies with `poetry install`

Run the application with `poetry run python3 weather_app/app.py`

# Docker Setup
Build docker image:
##
    docker build . -t weather_app

Note: Add SECURE_WEATHER_API_KEY in .env file

Run Docker container:
##
    docker run -p 7081:7080 --env-file <.env-file-path> weather_app:latest

# Kubernetes setup

Create Kubernetes Secrets to store SECURE_WEATHER_API_KEY value:

##
    kubectl create secret generic api-secret --from-literal=api-key=<API_KEY>

# Create Kubernetes Deployment & Service

Replace the DOCKER_HUB_USERNAME with the value in kubernetes/deployment.yaml

##
    image: <DOCKER_HUB_USERNAME>/weather_app:latest

# Create Kubernetes deployment:
##
    kubectl apply -f kubernetes/deployment.yaml
# Create Kubernetes service:
##
    kubectl apply -f kubernetes/service.yaml
