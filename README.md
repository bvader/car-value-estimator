# car-value-estimator

A simple Spring Boot application that simulates / calculates car market values 

To start the application:

`./mvnw spring-boot:run`


This Service is used by: https://github.com/bvader/cardatabase 

service is called using the pattern

http://localhost:8888/estimateValue?brand=Tesla&model=3&year=2019

If this sevice is called with query parameter brand=Ferrari it will cause a long running estimate.

example 
http://localhost:8888/estimateValue?brand=Ferrari&model=GTB&year=2019

which is the backend for:

The front end React application is at: https://github.com/bvader/carfront
