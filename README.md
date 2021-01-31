# microservices-eureka-zuul-zipkin

Eureka Naming Server - (REST-based server)
Service registration and service discovery are the two important features of the naming server. In the next step, we will set up a Eureka naming server.

Spring Cloud Config Server (External configuration in the Distributed system)  
Spring Cloud Config is Spring's client/server approach for storing and serving distributed configurations across multiple applications and environments.

Netflix Ribbon (Load balancing, Fault tolerance, Multiple protocols(HTTP, TCP, UDP), Caching and Batching)  
Netflix Ribbon is an Inter Process Communication (IPC) cloud library. Ribbon primarily provides client-side load balancing algorithms

Spring cloud Sleuth (Tracing the incoming request)
Sleuth is a tool from Spring cloud family. It is used to generate the trace id, span id and add these information to the service calls in the headers and MDC, so that It can be used by tools like Zipkin and ELK

Zipkin Distributed Tracing Server ( distributed tracing system) 
Zipkin is a Java-based distributed tracing system to collect and look up data from distributed systems. Too many things could happen when a request to an HTTP application is made. A request could include a call to a database engine, to a cache server, or any other dependency like another microservice.

Hystrix Server
Spring cloud helps to build fault tolerance system by implementing Netflix Hystrix.It is a latency and fault tolerance library designed to isolate points of access to remote systems, services and 3rd party libraries, stop cascading failure and enable resilience in complex distributed systems where failure is inevitable

Netflix ZuulAPI Gateway Server
Zuul acts as an API gateway or Edge service. It receives all the requests coming from the UI and then delegates the requests to internal microservices. So, we have to create a brand new microservice which is Zuul-enabled, and this service sits on top of all other microservices. It acts as an Edge service or client-facing service. Its Service API should be exposed to the client/UI. The client calls this service as a proxy for an internal microservice, then this service delegates the request to the appropriate service.


JSON Web Tokens, commonly known as JWTs, are tokens that are used to authenticate users on applications. This technology has gained popularity over the past few years because it enables backends to accept requests simply by validating the contents of these JWTS

run this command in programfiles/rabbitmdserver/sbin
rabbitmq-plugins enable rabbitmq_management

1. About employee-service
2. emp-org-service
3. service-service calls (Netflic Ribbon, FeignClient, Eureka Naming Server)
4. Authentication (Basic Auth ,OAuth)
5. Load Balancing (Netflic Ribbon, Zuul API Gateway)
6. APIGateway (Zuul API Gateway)
6.1 Moniterting - Actuator, Zipkin server
7. Tracking the incoming Requests(logging and Tracking)(sleuth, Zipkin server, )
8. Fault Tolerance (Hystrix)
9. Best practices

http://localhost:15672/#/channels -> RMQ guest/guest
http://127.0.0.1:9411/zipkin/     -> zipkin
http://localhost:8761/            -> Eureka
http://localhost:8080/employee/list  Employee Service
http://localhost:8090/employee/list  Employee org-service
http://localhost:8765/            -> Zuul API Gateway


These are the following things need to run end to end Services.
1. You should need to install and run RabbitMQ for managing Distributed Logging mechanism.
2. Need to run Zipkin server, for that follow the bellow steps
git clone https://github.com/openzipkin/zipkin
cd zipkin
# Build the server and also make its dependencies
mvnw -DskipTests --also-make -pl zipkin-server clean install
# Run the server
java -jar ./zipkin-server/target/zipkin-server-*exec.jar

kill running zipkin server then run the following cmds

C:\>SET RABBIT_URI=amqp://localhost  
C:\> java -jar zipkin-server-2.12.9-exec.jar  


Once if you setup these RabbitMQ and zipkin server, we are good to run end to end MS.