# Why System Monitoring Makes Your Life So Much Easier
*It can be a challenge as a developer, to keep track of your systems state and issues that might arise. Fixing said issues costs money and having to find the issues costs additionally, which is obviously something to limit in business. By utilizing Monitoring systems, you can minimize the time spend looking for problems and perhaps know about them before they even become an issue. That way you can immediately start fixing problems as they occur and save time in the process, which is beneficial for developer/support as well as customer.*

## Our problem and it's consequences
We’ve all been there, our system suddenly doesn’t function as intended and we have no idea why. Whether it crashes, runs slow or has unintended behaviour. Fixing this becomes quite the challenge at times. This kind of troubleshooting often becomes trial and error, until you find the source of your problem. Sometimes you’ll be unaware of the issue, which in turn makes your system slower, filled with exceptions and so forth. As a business point of view this is something to avoid. You can hire system operators to keep track of your system that can then notify developers of rising issues. But what if we told you, this could be automated? Then maintaining the software could be the developers job through the methodology [DevOps](https://github.com/datsoftlyngby/soft2018fall-lsd-teaching-material/blob/master/lecture_notes/10-DevOps%20and%20Monitoring.ipynb). For that we need automated system monitoring.  

## What is System Monitoring
System monitoring is a broad term, but generally speaking it allows for tools to analyze and monitor your system automatically. Otherwise we'd have to do it manually, which would be more costly and a lot less efficient.

Say your system has stopped responding, then you can have a system that constantly checks status. Whenever we don't get the expected HTTP-200 code, but instead get a 400 or 500 code, it then informs us of the issue but utilizing an alarm system. It can also help us monitor the performance, where we can keep track of ram usage and the amount of data being send and received by our system. It can be a prolonged process of setting up System Monitoring, but when done properly it will be worth it in the long term. 
Noget med at hvad man kan monitor. Dette inkl. personalized endpoints, http codes, ram usage osv. 

## Monitoring Tools
A short section about Grafana, Prometheus and one where we combine it. Alternatives will also be talked about.

- Her kan der være pros and cons for de individuelle tools. 
Prometheus

Grafana 

Prometheus + Grafana

![Monitoring design](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/Monitoring-design.JPG)

Other tools 

Manual Monitoring
Takes longer to config.

## Pros and cons with System Monitoring(Generelt)
Pros
1. system monitoring is much cheaper than having to monitor it manually.
2. limits maintainability, which is a huge cost when developing and delivering software.

cons
1. can be a challenge to set-up properly. 
2. it require knowledge of the system, i.e. the developer has to implement it, not the person in charge of monitoring (support etc.)

## Conclusion
Our problem is solved by utilizing well-known and well-documented tools, which allows us to quickly have monitoring up and running. It does require some planning and tinkering, but when its up and running, our knowledge of the system is much better. Where is, without monitoring we'd only see the surface of the software and only be aware of issues when someone tries to use a functionality and it fails, is slow or something third.

- Her skal vi reflektere ud over at konkluderer. The bigger picture. 

## References 
 1. https://www.researchgate.net/publication/267780070_Monitoring_Tools_for_Large_Scale_Systems - A list of tools for monitoring, written as a blog.
 2. https://github.com/datsoftlyngby/soft2018fall-lsd-teaching-material/blob/master/lecture_notes/10-DevOps%20and%20Monitoring.ipynb
 3. https://prometheus.io/docs/introduction/overview/
 4. https://blog.pandorafms.org/why-you-need-a-monitoring-system/
