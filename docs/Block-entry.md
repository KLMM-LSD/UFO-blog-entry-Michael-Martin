# System Monitoring
## Our problem and it's consequences

Lack of monitoring makes finding bugs/ other issues more difficult, meaning it will take more time and cost more resources. 

## What is System Monitoring

System monitoring is a broad term, but generally speaking it allows for tools to analyze and obviously monitor your system automatically. Otherwise we'd have to do it manually, which would be more costly and a lot less efficient. 

## What problems can System Monitoring create

The "problem" would be setting it properly up and making sure it measure and monitors the correct endpoints, so that we are sure that error will be found immediately. 

## How can you solve problems with System Monitoring

Say your system has stopped reponding, then you can have a system that constantly checks status. Whenever we don't get the expected HTTP-200 code, but instead get a 400 or 500 code, it then informs us of the issue but utilizing an alarm system. It can also help us monitor the performance, where we can keep track of ram usage and the amount of data being send and received by our system. 

## Pros and cons with System Monitoring

Pros
1. system monitoring is much cheaper than having to monitor it manually.
2. limits maintainability, which is a huge cost when developing and delivering software.

cons
1. can be a challenge to set-up properly. 
2. it require knowledge of the system, i.e. the developer has to implement it, not the person in charge of monitoring (support etc.)

## How did we solve our problem

Our problem is solved by utilizing well-known and well-documented tools, which allows us to quickly have monitoring up and running. It does require some planning and tinkering, but when its up and running, our knowledge of the system is much better. Where is, without monitoring we'd only see the surface of the software and only be aware of issues when someone tries to use a functionality and it fails, is slow or something third. 

## References

Her er vores kilder, husk at sætte en reference i selve teksten, hvor kilden bliver brugt. 

 1. https://www.researchgate.net/publication/267780070_Monitoring_Tools_for_Large_Scale_Systems - A list of tools for monitoring, written as a blog.
