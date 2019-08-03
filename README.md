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

 Build  
`./mvnw package -Dmaven.test.skip=true`

Get the Elastic Java APM agent  
`curl -O  https://search.maven.org/remotecontent?filepath=co/elastic/apm/elastic-apm-agent/1.8.0/elastic-apm-agent-1.8.0.jar`

Run cardatabase with APM
NOTE: `trace_methods` enables method tracing which reports all methods which is not recommended for production
Unix / Mac OS  
```shell_session
java -javaagent:./elastic-apm-agent-1.8.0.jar \
-Delastic.apm.server_urls="http://localhost:8200" \
-Delastic.apm.secret_token=“mysecrettoken” \
-Delastic.apm.service_name="car-value-estimator" \
-Delastic.apm.trace_methods="com.bvader.estimator.*" \
-jar target/car-value-estimator-service-0.1.0.jar
```

## To Deploy to Cloud foundry and Leverage Elastic APM

See the Cloud Foundry Elastic APM Document

https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-elastic_apm_agent.md

Create the user provided service

`cf cups elastic-apm-service -p '{"server_urls":"https://my-apm-server:8200","secret_token":"my-secret-token"}'`

`cf push -f car-value-estimator-manifest.yml`

The front end React application is at: https://github.com/bvader/carfront
