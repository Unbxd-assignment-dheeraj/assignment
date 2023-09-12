Design Document: https://docs.google.com/document/d/1aOlineALhiX35pJ-xlQ0hHZwfWuef7By6sfbSzZIl9s/edit?usp=sharing

Commands:

To run on kubernetes: 

    Build docker image from Dockerfile: docker build -t flask-app .   

    Tag the docker image built: docker tag flask-app dheerajsreddy/flask-app

    Push the docker image to dockerhub: docker push dheerajsreddy/flask-app  

    Create a kind cluster using the specified configurations: kind create cluster --name apparel --config=config.yaml  

    1)Apply the deployment manifests: kubectl apply -f flask.yaml,cache.yaml,database.yaml  

    Set the hostname to access locally: sudo nano /etc/hosts and set 127.0.0.1 to apparel.com
    
    2)Using helm for deployment(flask-chart directory):

    Command: helm install flask-app .  

    To run:
    
    Port forward: kubectl port-forward service/flask-service 5000:5000

    Access using browser or postman or curl in terminal using :

    curl http://localhost:5000/

    or http://apparel.com:5000/

    to access the services

    POST :

    http://localhost:5000/data_ingestion

    GET:

    http://localhost:5000/product/06775807C

    http://localhost:5000/category

    http://localhost:5000/category/women

    http://localhost:5000/category/men

    http://localhost:5000/category/men/New Arrivals

    http://localhost:5000/category/women/Work

    http://localhost:5000/search?q=deny designs taos tile marsala bed in a bag set

    http://localhost:5000/search?q=80002327

    http://localhost:5000/monitor

    To view:
    kubectl get pods
    kubectl get deployments
    kubectl get services

    To stop :
    kubectl delete deployments
    kubectl delete services


To check if the containers run using docker compose, go to Backend/src folder change the urls for database and redis from postgres-service and redis-service to database-container and redis-container in app.py and go to Backend folder:

To build docker image:docker-compose build 

To start the containers and the services:docker-compose up

To stop running containers: docker-compose down

To run locally go to Backend/src folder change the urls for database and redis from postgres-service and redis-service to localhost in app.py.

Run python3 app.py 

Start the redis server in another terminal using command redis-server. 

redis cli and can be accesed using command redis-cli :

FLUSHALL - to delete all keys

keys * - to get all keys

GET keyname - to get particular key

Make get and post requests using postman or curl in terminal

To run the postman collection (for api test cases):

newman Data.postman_collection.json 

