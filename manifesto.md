# The Agile Operations Manifesto

As with the Software Manifesto,while there is value in the items on
the right, we value the items on the left more:

* Stability over New Technolgies
* Scalability over speed of deployment
* Testing and Automation over "just get it done"
* Monitoring from the start over Monitoring as an after-thought

## Stability over New Technologies

New technology is important. If it wasn't for the constant evolution of software and approaches to it then most of the tooling that we have available to us, from Continuous Integration Tooling to Configuration Management, wouldn't exist.

That being said, I've seen a large number of technologies being implemented in production systems in the past two years because they are "the new hotness", and in many cases this has led to instability on the platform.  This frequently stems from the fact that the technology is so new that whilst it works perfectly well on a small scale such as a developer's or system administrator's laptop either the original design wasn't meant to roll out to hundreds or thousands of hosts, or no one has actually tried running it at scale within a dynamic environment such as AWS or Azure and therefore configuration flags relating to things such as memory and task management haven't been truly put to the test under a production load.

```
Learning is good and we should always strive to improve the tools that we use, however, in a world of zero downtime and 24x7 customer experience, we should never sacrifice platform integrity and stability because "everyone else is doing it".
```

## Scalability over speed of deployment

James Smith from DevOpsGuys has a saying which I'll paraphrase here: "You can put in the best pipeline ever, and deploy 11 times a second just like Amazon, but if your code quality is poor then you're just shipping the same rubbish but faster".

```
Only Amazon and other companies operating on that scale such as Facebook or Google need to ship 11 times a second.
```

If you're currently shipping twice a year to production, then try and get to a point where you're deploying once every quarter, then once a month, then once a week and so on.  It may be that you get to a point where there are so many code changes being made to your application that you have a need to ship once an hour or once a minute even, however, you should always be shipping code that adds to the stability of the platform and improves the experience of your customers instead of looking to have a statistic on number of deployments/minute that you can brag about at conferences.

## Testing and Automation over "just get it done"

So often in the operations world, there is pressure to "just get it done" and get the platform up and running.  This can come from a variety of sources and the pressure often comes down to the same reason - a deadline has been promised without thinking about the hardware side of things.

If I were to suggest to a scrum master that there was no need to test the code that was being written and deployed because we "just need it ready" in time for an arbitrary date/time, the scrum master would (I hope!) push back and say that was simply unacceptable.

So why do we allow our Operations Teams to deploy server configuration that is untested or make changes manually  to a production system "to get it live"?

```
Tools such as ServerSpec, Test Kitchen and the numerous linting tools enable Operations Teams to run Test Driven Development cycles of "Infrastructure as Code", and by adding simple monitoring tools into the mix it is even possible to perform automated integration testing, improving the integrity and stability of the platform.
Your software has been proven to work better when fully tested, so why wouldn't you want to fully test your infrastructure too?
```

## Monitoring from the start over Monitoring as an afterthought

So often in the past 16 years of systems administration and design, I've seen people add monitoring as an afterthought, often leaving huge gaps in alerting and monitoring on production platforms leading to outages that could easily have been avoided.

If Operations Teams work with the developers to help them instrument their code through tools such as StatsD, to monitor critical paths using cucumber-nagios or hook into message queues via Sensu or similar, then the application performance can be monitored closely and deviations from the normal, acceptable range can be detected using Graphite or and of the other StatsD-compatible tools out there.

Tools such as ELK or Greylog2 allow analysis of application logs and correlation between events in monitoring and on the platform providing you with in-depth analysis of not only what happened, but giving you a fairly good idea of why it happened

There are also an entire plethora of tools out there to test your security and report back any potential ingress points or intrusion attempts

```
Monitoring is the thing that will ensure you spot issues before they become emergencies.  It is your first line of defence against platform instability and customer satisfaction, and it should be a first-class citizen in every project that you undertake.
```
