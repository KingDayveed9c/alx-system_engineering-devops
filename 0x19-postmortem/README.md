Postmortem

Server requests failure report
Last week, it was reported that the platform was returning 500 Error on all requests made on the platform routes, all the services were down. 90% of the users were affected. The root cause was the failure of our master server web-01.

Timeline
The error occurred on 25th February, 2023 at 1000 hours (West Africa Time) when James Stallon saw the master server lagging in speed. Our engineers on call disconnected the master server web-01 for further system analysis and channeled all requests to client server web-02. This issue was solved on Sunday 26th February, 2023 at 2200 hours (West Africa Time).

Cause and Resolution
The platform is served by 2 ubuntu cloud servers. The master server web-01 was connected to serve all requests, and it stopped functioning due to memory outage as a result of so many requests because during a previous test, the client server web-02 was disconnected temporarily for testing and was not connected to the load balancer afterwards.
The issue was fixed when the master server was temporarily disconnected for memory clean-up then connected back to the load balancer and a round-robin algorithm was configured so that both the master and client servers could handle an equal amount of requests.

Prevention against such problem in future
Choose the best load balancing algorithm for your programs
Always keep an eye on your servers to ensure they are running properly
Have extra back-up servers to prevent your program from completely going offline during an issue
