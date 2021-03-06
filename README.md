# Overview
This sample ecommerce application(sells only a few books:) for now) is built with Spring Boot 2.3.1 on Spring WebFlux stack. This application uses Azure Cosmos DB SQL API with the Java SDK 4.0, whish is based on the reactor core.
The current version has the following capabilities:
* Display catalog
* Add items to cart
* Remove items from cart
* Check out
* Order creation, confirmation and history
* Order processing with change feed processor
* Infinite scrolling
* Unit testing reactive streams with JUnit, StepVerifier/TestPublisher and Mockito

I will be adding additional capabilities as time permits. Check out the project page associated with this repo for more details. 


Additionally, I plan to decompose the application into microservices and leverage spring cloud capabilities to address some of the distributed system challenges.

# Instructions

## First:
 * Java 8
 * Maven
 * Create a Cosmos DB SQL API Account. 
 * Clone the repo

## Then:
* Update the cosmos DB endpoint, key and locations information in application.properties
* mvn spring-boot:run from the project base
* On startup the application creates 3 cosmos collections, namely book, order, cart and order-lease. Each one will be configured with 400 RUs.
* Access the WebApp at http://localhost/ebooks/index
* Default user accounts customer1/customer1 and customer2/customer2
* If you prefer docker:  
  * mvnw package 
  * docker build -t <YOUR REPO>/store .
  * docker run -p 80:80 -e database.endpoint=<URI> -e database.key=<PRIMARY KEY> -t <YOUR REPO>/store
  * Access the WebApp at http://localhost/ebooks/index with the default accounts mentioned previously
* If you want to just get the app up and running, you could use my container:
  * docker run -p 80:80 -e database.endpoint=<COSMOS_ENDPOINT> -e database.key=<COSMOS_KEY> -t ravitella/store
  * Access the WebApp at http://localhost/ebooks/index with the default accounts mentioned previously 

* This is the home page

 ![Image](BookStore.png)

