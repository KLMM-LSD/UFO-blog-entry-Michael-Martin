# Why System Monitoring Makes Your Life So Much Easier
*By Michael Veilis and Martin Hansen*

*It can be a challenge as a developer, to keep track of your system’s state and issues that might arise. Fixing said issues costs money and having to find the issues costs additionally, which is obviously something to limit in a business. By utilizing Monitoring systems, you can minimize the time spend looking for problems and perhaps know about them before they even become an issue. That way you can immediately start fixing problems as they occur and save time in the process, which is beneficial for developer/support as well as customer.*

## Preface 
This blog is based on a school project developed for a course in “Large System Development”. Our assignment was to make a clone of the popular site [Hackernews](https://news.ycombinator.com/), which in turn should be able to manage large amounts of data, up towards 15 million requests during a semester. The target group for this blog are students attending the same course. Our focus lies in Grafana and Prometheus - and how they helped us fix our monitoring issues.

## Introduction
A system can malfunction in a lot of ways. Whether it crashes, runs slow or has unintended behaviour. Fixing this becomes quite the challenge at times. This kind of troubleshooting often becomes trial and error, until you find the source of your problem. Sometimes you’ll be unaware of the issue, which in turn makes your system slower, filled with exceptions and so forth. As a business point of view this is something to avoid. You can hire system operators to keep track of your system who can then notify developers of rising issues. But what if we told you, this could be automated? Then maintaining the software could be the developers job through the methodology [DevOps](https://www.atlassian.com/devops). For that we need automated system monitoring.

## What is System Monitoring
System monitoring is a broad term, but generally speaking it allows for tools to analyze and monitor your system automatically. Otherwise we'd have to do it manually, which would be more costly and a lot less efficient.

Say your system has stopped responding, then you can have a monitoring system that constantly checks server status. Whenever we don't get the expected HTTP-200 code, but instead get a 400 or 500 code, it then informs us of the issue but utilizing an alarm system. It can also help us monitor the performance, where we can keep track of ram usage and the amount of data being send and received by our system. It can be a prolonged process of setting up System Monitoring, but when done properly it will be worth it in the long term.

System monitoring is your friend when it comes to the errors, that you inevitably will encounter as a developer. A properly configured automated system monitoring will react immediately upon finding an error and can even act in a proactive manner. For instance, it can be set up to 1) Fix an error right as it occurs, 2) Alert the system admin / developer whenever a certain condition is met, 3) It could even notify the support department and much more. That, to us, sounds much better than having a customer call early in the morning, because their system is failing.

As mentioned before one of the things that our system could monitor for us, could be our servers status - by checking the HTTP-code on a regular basis (let’s say once every 2 minutes). But this is merely the surface level. Various tools has a bunch of pre-defined metrics that you can track, visualize and otherwise utilize. However, you can also create your own custom metrics defined in your code. There’s a countless number of metrics that you could monitor, but some of the more common could be:
- Uptime/availability (usually percentage of all time)
- Mean response time (average time to serve answer)
- Mean time to recover ( time to recover after outage)
- Failure frequency (number of failures/ timeouts over time)

If you need any inspiration for what metrics to monitor, check out [wikipedia](https://en.wikipedia.org/wiki/Service-level_agreement#Common_metrics) and this [article](http://rbsla.ruleml.org/docs/GI-Proceedings-80-2.pdf). You don’t need a fancy tool to do system monitoring, it can definitely be done by ourselves from scratch using loggers and email alerting. It would however, make sense to use one of the many options of tools to do the monitoring, instead of spending a lot of time making an all in all worse system yourself. The higher complexity the system has, the harder it becomes to keep track of each method of functionality, endpoint etc. For that, it makes sense to use one of following tools to help you configure each metric and visualize the performance of the system.
