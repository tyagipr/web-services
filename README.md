## Steps to run the services on kubernetes

clone this project in the VM (control node)

1. first setup database - postgresql
2. pull image from docker hub - `docker pull postgres`
3. Run docker image using this command- `docker run -d -p 5432:5432 -e POSTGRES_PASSWORD=web-services-g7 -e POSTGRES_DB=webservices --name postgres-container  postgres`
4. Create a pod of postgres image in kubernetes -
     4.1 `kubectl apply -f db-postgres-deployment.yaml`

5. Now let's move to deploy the services
     create docker image of these services first - `docker build -t urlshortener-app .` , `docker build -t auth-app .`
     deploy authentication-app docker image using auth-api-deployment.yaml - `kubectl apply -f auth-api-deployment.yaml`
     deploy urlshortener-app docker image using urlshortener-api-deployment.yaml - `kubectl apply -f urlshortener-api-deployment.yaml`



6. check the running pods -  `kubectl get pods`
   
   
     


