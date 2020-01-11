# car-value-estimator

A simple Spring Boot application that simulates / calculates car market values

To start the application:

`./mvnw spring-boot:run`

This Service is used by: https://github.com/bvader/cardatabase

Which is the backend for:

The front end React application is at: https://github.com/bvader/carfront

The `car-value-estimator` service is called using the pattern

`http://localhost:8888/estimateValue?brand=Tesla&model=3&year=2019`

If this sevice is called with query parameter brand=Ferrari it will cause a long running estimate.

example  
`http://localhost:8888/estimateValue?brand=Ferrari&model=GTB&year=2019`

## To start the application with Elastic Java APM Agent

Run the build and run script you can change the agent verion if you whish, or add other optiosn. This will start the service expecting all other services and the ELK stack runing on `localhost`

`./run-with-agent.sh`

## To Deploy to Cloud foundry and Leverage Elastic APM

See the Cloud Foundry Elastic APM Document

https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-elastic_apm_agent.md

Create the user provided service

`cf cups elastic-apm-service -p '{"server_urls":"https://my-apm-server:8200","secret_token":"my-secret-token", "enable_log_correlation":"'true'"}'`

`cf push -f car-value-estimator-manifest.yml`

The front end React application is at: https://github.com/bvader/carfront
