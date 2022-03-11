# nodejs-express-govuk-mysql

REST API
---
This application provides a frontend for the REST API: https://github.com/shaunganley/java-dropwizard-swagger-jdbc
1. Follow the steps in the above link to run the REST API


How to start the nodejs-express-govuk-mysql application
---

1. Run `npm install` to build your application
1. Start application with `npm start`
1. To check that your application is running enter url `http://localhost:3000/employees`

Config
---

1. You can change the URL of the REST API by setting the restApiUrl environment variable

Build and run the service through docker
---

You can build in a number of ways using docker and integrate it with a database, these are listed below:
pre-requisite = docker and docker compose are installed in your local system.
                your docker image for the backend api is available locally 
                (the web ui has a dependency on this) and running.

1.  Ensure the environment variables are correct for your chosen db you can enter these as 
    additional arguments on the docker build command. NOTE if you don't pass these in your 
    env vars will be blank, the env var references from the repo refer to github secrets 
    which are used in the cloud deployment but not available for local repository work.

    Run "docker build -t <service name given + optional tag> . --build-arg API_URL=<BACKEND API URL>" from your src directory.
    This will read from your docker file, build the environment required for the 
    image, build your service and create the image locally.
    
    Use "docker images" to verify your image is available after running the above command.
    
    Now run "docker run -p <chosen port to host locally on your machine>:3000 <your image 
    name given>", this will then spin up your image and host on the given port.
    
2.  You can also deploy by docker compose which handles the network traffic between 
    containers also will deploy a mysql container also.
    pre-requisite = ensure your docker image is available or build with docker compose, ensure 
    that name is in the image name for docker compose file.
    set you API_URL environment variable (you will notice the docker compose file creates container and host names meaning the value of this would be http://academy-api:8080/ if not altered)
    run "docker compose up" from the src directory, this spins up both the web,api and a mysql db instance.
    
    Next log onto your db instance and follow the commands under "Database".
    
    Done....the service should be able to operate as expected.      
    