# REST Fundamentals:  
##### Properties of a RESTful Architecture:  
* Heterogeny - the ability of the application to seemlessly interoperate with other participants regardless of language or platform.  
* Scalability: 
  1. limits the amount of complexity that exists between compononents in a distributed system. Enabling the complexity of the overall system to scale much past the limits of a typical architectural structure.
  2. enables an application to more efficiently manage requests and scale out horizontally when needed.  
* Evolvability - the ability of restful clients and services to evolve independently of one another.  
* Visibility - enables value added components, such as montioring applications, to operate directly without needing access to any hidden or propriety state.  
* Reliability - more reliably cover from failures.  
* Efficiency - enables multiple components such as proxy servers and caches to participate in the handling of requests. These intermediaries have the effect of taking load away from your server. Additionally, it keeps your server from having to manage a bunch of shared state, therefore it is able to manage its own resources more efficiently. 
* Performance - in the same way caches can improve the efficiency of a resful application, they can also greatly improve the speed in which a response can be delivered to a user agent, thereby improving the overall perceived performance of your application.
* Manageability - a restful application can be more easily managed bc the interactions between components happen in a highly consistent and highly visible way, therefore management tools can have a much greater impact.  

##### What REST is NOT:  
* RPC
  * REST is not a way to call methods over a network without the overhead of SOAP and WSDL.
* HTTP
  * While most current RESTful systems are built using HTTP, an architecture implemented on top of HTTP is not inherently RESTful.  
* URIs
  * Largely because of the frameworks on which they are built, many RESTful systems have clean URL("cool URLs"). However, this not a requirement for REST.
  * Hyper-focus on URIs can actually make designs non-RESTful.
##### What REST is:  
* Stands for "Representational state transfer"  
* First introduced in 2000 by Roy Fielding as a part of his doctoral dissertation.
* Intended for long-lived network-based applications.

##### REST and SOAP:  
* Many people think of REST as "something that isn't SOAP"
* SOAP (and WSDL) is an implementation detail for RPC-style systems
* REST is juxtaposed with RPC.  

##### REST and RPC:
![](Images/2019-11-29-16-35-51.png)  

##### REST and HTTP:  
![](Images/2019-11-29-16-41-46.png)  




