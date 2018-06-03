# Circuit Breaker

Circuit breaker is a design pattern in software engineering to detect failure in service and prevent the service from trying to perform action that is doomed to fail (until it is safe to retry).  


Example: An service (or an application) connects to a database 100 times per second and the database fails. The service designer does not want the same error reoccur constantly and want to handle service degradation quickly and gracefully without waiting for TCP connection timeout. 

An implementation of a circuit breaker needs to keep the state of the connection over a series of requests. The logic to detect failures must be kept separate from the requests. An approach would be to update the states asynchronously from the processing of requests. In a cluster environment, the state of the service should be exposed to all nodes in the cluster. This can be done via periodic updates to a persistant storage layer, e.g., redis. Before the external service is accessed by the service, the current state in the persistant storage should be retrieved and checked. 

Here is a bunch of articles in this topic. 

- [Making the Netflix API More Resilient](https://medium.com/netflix-techblog/making-the-netflix-api-more-resilient-a8ec62159c2d)
