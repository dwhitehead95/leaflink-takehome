# LeafLink Take Home

Install dependencies with `poetry install`

Run the application with `poetry run python3 weather_app/app.py`

 # Summary
 Thank you for taking the time to review my submission. I was able to run the docker container and spin up the application locally, however my laptop is managed/monitored by my current company so I was unable to completely test the Kubernetes setup, although I believe I completed the first two of the four requests. As mentioned in our earlier conversation I have not worked with Kubernetes much so teaching myself how to create a deployment and service took the weekend, and I ran out of time to learn the other requirements needed for scaling. If I'm not selected to move along I'd like to say thank you for pushing me to learn more about Kubernetes it was fun! The app is pretty cool as well, I originally used gunicorn as the WSGI before realizing that wasn't the request so I apologize if a few of the depndencies look unused. I did not have time to clean them up. Please let me know if you have any questions. Thanks

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
