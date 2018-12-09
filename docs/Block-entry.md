# Why System Monitoring Makes Your Life So Much Easier
*By Michael Veilis and Martin Hansen*

*It can be a challenge as a developer, to keep track of your system’s state and issues that might arise. Fixing said issues costs money and having to find the issues costs additionally, which is obviously something to limit in a business. By utilizing Monitoring systems, you can minimize the time spend looking for problems and perhaps know about them before they even become an issue. That way you can immediately start fixing problems as they occur and save time in the process, which is beneficial for developer/support as well as customer.*

## Our problem and it's consequences
We’ve all been there, our system suddenly doesn’t function as intended and we have no idea why. Whether it crashes, runs slow or has unintended behaviour. Fixing this becomes quite the challenge at times. This kind of troubleshooting often becomes trial and error, until you find the source of your problem. Sometimes you’ll be unaware of the issue, which in turn makes your system slower, filled with exceptions and so forth. As a business point of view this is something to avoid. You can hire system operators to keep track of your system that can then notify developers of rising issues. But what if we told you, this could be automated? Then maintaining the software could be the developers job through the methodology [DevOps](https://github.com/datsoftlyngby/soft2018fall-lsd-teaching-material/blob/master/lecture_notes/10-DevOps%20and%20Monitoring.ipynb). For that we need automated system monitoring.  

## What is System Monitoring
System monitoring is a broad term, but generally speaking it allows for tools to analyze and monitor your system automatically. Otherwise we'd have to do it manually, which would be more costly and a lot less efficient.

Say your system has stopped responding, then you can have a monitoring system that constantly checks server status. Whenever we don't get the expected HTTP-200 code, but instead get a 400 or 500 code, it then informs us of the issue but utilizing an alarm system. It can also help us monitor the performance, where we can keep track of ram usage and the amount of data being send and received by our system. It can be a prolonged process of setting up System Monitoring, but when done properly it will be worth it in the long term.

System monitoring is your friend when it comes to the errors, that you inevitably will encounter as a developer. A properly configured automated system monitoring will react immediately upon finding an error and can even act in a proactive manner. For instance, it can be set up to 1) Fix an error right as it occurs, 2) Alert the system admin / developer whenever a certain condition is met, 3) It could even notify the support department and much more. That, to us, sounds much better than having a customer call early in the morning, because their system is failing.

As mentioned before one of the things that our system could monitor for us, could be our servers status - by checking the HTTP-code on a regular basis (let’s say once every 2 minutes). But this is merely the surface level. Various tools has a bunch of pre-defined metrics that you can track, visualize and otherwise utilize. However, you can also create your own custom metrics defined in your code. There’s a countless number of metrics that you could monitor, but some of the more common could be:
- Uptime/availability (usually percentage of all time)
- Mean response time (average time to serve answer)
- Mean time to recover ( time to recover after outage)
- Failure frequency (number of failures/ timeouts over time)

If you need any inspiration for what metrics to monitor, check out [wikipedia](https://en.wikipedia.org/wiki/Service-level_agreement#Common_metrics) and this [article](http://rbsla.ruleml.org/docs/GI-Proceedings-80-2.pdf). 
You don’t need a fancy tool to do system monitoring, it can definitely be done by ourselves from scratch using loggers and email alerting. It would however, make sense to use one of the many options of tools to do the monitoring, instead of spending a lot of time making an all in all worse system yourself. The higher complexity the system has, the harder it becomes to keep track of each method of functionality, endpoint etc. For that, it makes sense to use one of following tools to help you configure each metric and visualize the performance of the system.

## Monitoring Tools
Monitoring is nothing new and has always been relevant for IT systems, it’s therefore not a surprise that a lot of tools has been developed for this exact purpose. Monitoring tools each vary in functionality; some are good in terms of network monitoring, some look at general performance and others look at frequency of errors etc. A system could perhaps report to the support division and another system could report directly to the developer, depending on whose job it is to fix said problem. Some tools provide passive monitoring, meaning the problem gets fixed after it happens, this could be a dashboard.  Other tools provide active monitoring, which means we solve the problem as it occurs, this could be an alarm system. Our focus lies in what we’ve personally used for a large system project. For monitoring we utilized two tools, Grafana and Prometheus.

### Prometheus
Prometheus is an open-source systems monitoring and alerting toolkit originally built at SoundCloud and is now a member of the Cloud Native Computing Foundation(CNCF) as the second hosted project, after Kubernetes.

The way Prometheus has been used in our project was to find some relevant targets and expose them as metrics, as seen below:
![Prometheus](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/Prometheus.JPG)

We decided to expose three targets, which can be pulled via service discovery or config. Here we looked at metrics such as response time, amount of requests, HTTP-500 counter etc. This is very customizable and allows you to track almost whatever you want to. 

A way to display the data of the metrics via graphs can be done from a tool called Gafana.

### Grafana 
Grafana is a tool that allows you to query, visualize, alert on and understand your metrics no matter where they are stored. It lets you create dashboards which can be explored and shared with team members and foster a data driven culture.

So in our project we display and monitor specific metrics exposed from prometheus, which is possible by creating a dashboard to hold these graphs, as seen below:
![Grafana](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/Grafana.JPG)

Some graphs has more value than others but by doing this we have a great way of monitoring the most critical parts in the functional and non-functional parts of the program.
For instance, we have the most important one called latest id, which is monitoring all the input data that is being fed into our program and how many there are atm. We also have a graph for uptime in the frontpage to make sure it’s always running at high frequency.

The way Grafana makes it possible for this to happen is through configuration with the [PromQL](https://prometheus.io/docs/prometheus/latest/querying/basics/) language which uses the HTTP API.

### Prometheus + Grafana
Prometheus and Grafana works really well with each other as described earlier and is also seen in the picture below. The way both Prometheus and Grafana is started is via a [docker-compose.yml](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/Docker-compose.JPG) file, this takes the [prometheus.yml](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/PromYaml.JPG) file which is the configuration file for prometheus that tells how to use prometheus in our program. Aside from Prometheus and Grafana working well with each other, some other tools can also work very well with prometheus. An Alertmanager for alerting via mail for instance, if something should go from with the system. A Service discovery like Kubernetes for discovering targets and a Pushgateway for Short-lived jobs. We only used Prometheus and Grafana and a bit with the alertmanager, where we first tried to alert via Discord but decided it didn’t work with discord and just configured it to alert us via Email.

![Monitoring design](https://github.com/KLMM-LSD/UFO-blog-entry-Michael-Martin/blob/master/Resources/Monitoring-design.JPG)

### Alternative Tools
While our experiences with Grafana and Prometheus were satisfactory, there’s obviously a bunch of alternatives that perhaps are better in other ways. Some alternatives to Prometheus are Nagios, Sensu, OpenTSDB, InfluxDB etc. and you can read more [here](https://www.google.com/url?q=https://prometheus.io/docs/introduction/comparison/&sa=D&ust=1544374532076000&usg=AFQjCNFPnyUdzobm6Uait-zTTZbRoilR-w) in terms of pros and cons. Alternatives to Grafana could be Kibana or Graphite, for when it comes to visualizing your data. It is all about finding the tool best suited for your particular need. You don’t have to limit yourself to one monitoring system, it can be very beneficial to combine multiple tools. 

### Manual Monitoring
Just like with general developing, we use tools whenever it’s beneficial. While we could make all functionality from scratch, but often times it makes sense to use a 3rd party tool to handle that task. But sometimes it is more simple to do it yourself. If the functionality that you’re looking for is rather simple, you might save time doing it yourself, rather than relying on a tool. Monitoring could be handled by a simple logging system, perhaps with a built in alert system for whenever the logged information of high enough importance. Later on an email alert system might be added, then something third and so on. Eventually you might end up in a situation where it takes a lot of effort to maintain your own monitor system. This is where the tools come in handy, when a more thorough monitor system is needed and the complexity got too much to handle etc.

## Conclusion
Our problem is solved by utilizing well-known and well-documented tools, which allows us to quickly have monitoring up and running. It does require some planning and tinkering, but when its up and running, our knowledge of the system is much better. Where is, without monitoring we'd only see the surface of the software and only be aware of issues when someone tries to use a functionality and it fails or is too slow etc. This makes maintainability of your system much cheaper, faster and potentially much less frustrating. It does however require knowledge of the system to automate, so don’t expect your support guy to be able to do it all if he hasn’t worked on the project. It is certainly something we, and many others, can recommend. Monitoring is often expected when providing a service for another company (usually through contract), so why not make it easier for yourself?

## References 
1. https://www.researchgate.net/publication/267780070_Monitoring_Tools_for_Large_Scale_Systems - A list of tools for monitoring, written as a blog.
2. https://github.com/datsoftlyngby/soft2018fall-lsd-teaching-material/blob/master/lecture_notes/10-DevOps%20and%20Monitoring.ipynb - Lecture notes from LSD session 10.
3. https://prometheus.io/docs/introduction/overview/ - General overview of prometheus.
4. https://grafana.com/ - General overview of Grafana
5. https://blog.pandorafms.org/why-you-need-a-monitoring-system/ - blog of why to use System Monitoring.
6. https://www.opsview.com/resources/automation/whitepapers/it-monitoring-and-automation - General about monitoring of IT systems
7. https://prometheus.io/docs/introduction/comparison/ - for comparision with other tools
8. https://prometheus.io/docs/prometheus/latest/querying/basics/ - PromQL description
