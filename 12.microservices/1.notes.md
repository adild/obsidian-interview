server.port = 0 -> dynamic address of services

restTemplate is blocking in nature.
it uses one thread to receive request from one service and will wait until response is back from another service. So this thread is blocked from doing anything and is waiting for the response.


Netflix feignclient

add the dependency.
create interface -

@FeignClient(name = "abc", url = "http://localhost:8081/address-api/api/")
public interface AddressClient{

	@GetMapping("/address/{id}")
	Address Response getAddressByEmpId(@PathVariable("id") int id)
}

use the above interface in other classes -

EmployeeServiceImpl.java

@Autowired
private AddressClient addressClient;

AddressResponse res addressClient.getAddressByEmpId(id);

Load balance -
ribbon from netflix feign client is removed..
use spring cloud load balancer as a load balancer. it is used on client side.

server side load balancer is not good.
need to create a different service for load balance.
2 calls required for communication ie from client -> load balancer service -> server.
single point of failer load balncer service is down, everything in microservice is down as well.
need maintainance cost and separate team.

to solve above problem, we have service discovery -

- Service Discovery 
service discovery maintains ip addresses and port numbers of every other microservices.

- Server side Service Discovery -

![[Pasted image 20250716124112.png]]

- Client side Service Discovery -
lets say serviceA wants to call serviceB.
It will call Discovery Service which has all instances(ip address and port numbers) of services.
Discovery Service sends back all serviceB instances to serviceA.
Now serviceA is acting as a load balancer and will call any one instance of serviceB.
So there is no load balancer, client itself doing load balancing.
![[Pasted image 20250716142711.png]]

when serviceA calls Discovery Service for the first time, it will store instances on its side as a cache.
So it wont call multiple times to Discovery Service.
can we still improve this?
a background thread is use to call Discovery Service to get instances of other services.
netflix eureka is a library to implement client side Discovery Service.

- Eureka Discovery Service -
All microservices will connect to eureka during start up, and fetch the eureka registry(info about all registered service urls). they further use these  urls to connect to each other.

practical -
create a new springboot project and add the 
watch from this - https://youtu.be/1uNo1NrqsX4?list=PL3NrzZBjk6m_n8QZCdnF7Yax36cqWkO9j&t=707 till 17:43
skip from 17:43 to 30:30
watch from this - https://youtu.be/1uNo1NrqsX4?list=PL3NrzZBjk6m_n8QZCdnF7Yax36cqWkO9j&t=1829

![[Pasted image 20250716161410.png]]

after running eureka goto - localhost:8761/eureka/apps
remember - first hit/refresh -> localhost:8761 -> this is ui -> localhost:8761/eureka/apps
its a useful for getting info. Its basically a registry.
it will show details of instances up and running.
leaseInfo - 
	- service will send heart beat every 30 secs to eureka. 	
		- lease-renewal-interval-in-seconds property - default is 30, we can change it using this property
	- if for 90 secs its not sending heart beat then service is deregistered from eureka register
		- lease-expiration-duration-in-seconds property - default is 90, we can change.

- TCS/IP monitor - 
https://www.youtube.com/watch?v=ZcM3e_zp6Tk&list=PL3NrzZBjk6m_n8QZCdnF7Yax36cqWkO9j&index=7&t=3019s

- Actuator - https://www.youtube.com/watch?v=FnxXp1m1TTw&list=PL3NrzZBjk6m_n8QZCdnF7Yax36cqWkO9j&index=9&t=162s

