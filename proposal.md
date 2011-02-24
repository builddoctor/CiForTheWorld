We understand it's a lot of ground to cover and would like to request a session of 90 minutes to both demonstrate and explain the concepts.

Even then we will have to be firm on timings.  With a pair of presenters we will be able to talk, while fiddling with the environment.  Our plan is to make everything that we can be self-contained, so any failings are our fault.  We will attempt to record the demonstrations so we can have a fall-back plan.  A
particular challenge that we will face will be to make video readable on the big screen. It might be easier to take many screenshots, so we can highlight relevant text, and display it at a larger font size.

Ideally we'd be able to have an iPad/laptop for the slides and a laptop for the demonstrations, but I'm not sure how feasible that will be until we can talk to the A/V staff at the conference.

The session will run as follows:

00:00 - 00:10 Introduction, latecomers and schedule.

It'll be hard to summarize all the ground that we have to cover, so we'll try and push that into each session.  What is important is to demonstrate (however briefly) the application that is our vehicle for the talk.  

We'll make the examples related to deploying this application - a simple Ruby application (simple because it's a demo and we don't want to provoke Murphy, and Ruby because it can have annoying dependencies - which chimes with our message that you're not done until it's deployed in production).  We mention many technology options below, but will only demonstrate one - that's subject to change at the moment because we have no vendor alliances (we might like some more than others, and we both run consulting companies, but apart from that ...)

* 00:11 - 00:20 Installation of the operating system. *

We might as well diverge at the start.  The production operating system install generally comes later in the project lifecycle, but we're going to front-load it because a) it's much easier these days and b) we want system integration from the start. 

Similar to building software, installing an OS depends on several parts to be available: 

- the base operating (by CD, DVD or PXE boot)
- the OS packages that need to be installed (RPM, Debian, ...)
- the configuration of the base OS (JEOS = Just enough Operating system) (kickstart, jumpstart, preseed)
- the role of virtualization and cloud in this

We'll be using the Vagrant tool to build virtual machines, with the VeeWee wrapper that makes bootstrapper easier. 
We can check this in as 'source code' in a local GIT repo and run basic tests using cucumber to verify the basic functionality

* 00:21 - 00:30 Configuration Management. *

After the initial install, usually people start entering manual commands on the system. This often makes the system developer friendly and scares people to do the process often. A better way of doing this is by using a configuration management system.

We plan to to use the Chef tool to make a basic 'recipe' ( Chef's term for a configuration to be applied to our brand new VM;  we'll also have one we prepared earlier; you do learn things from daytime TV!).  We'll check that into the Git version control system, so we can track changes.  We've already turned the tables on traditional systems administration at this point; We could trash the VM at this stage and rebuild our VM from source, as long as we had the git sources.

Once we have the version control system running, we can start on the Continuous Integration.  We'll be using Jenkins (previously known as Hudson) to track changes to the files in our Git repositories. As we add testing to the mix, we'll add these to Jenkins, using the Rake build tool.

- this will show the basics of configuration management
- how it helps to make things repeatable (across environments)
- similarity between 'normal code'
- Why logging in to a server, is considered harmfull

* 00:31 - 00:45 Behavioral Monitoring * 

We're fond of the Cucumber BDD tool.  It can also be used for testing infrastructure, so we'll knock up some quick Cucumber scenarios that pertain to our infrastructure, to make sure that the machine is working correctly.  Then we'll show how those tests can be driven from Jenkins and the popular open source monitoring tool, Nagios (via the cucumber-nagios plugin).

- shows you that you can run tests against infrastructure similar to development

* 00:46 - 00:60 Application Development *

Now that we have the complete infrastructure (JEOS+ ruby) build, we'll take are of the other part: make a very simple Ruby on Rails application, and version control it in Git. We'll add some trivial unit tests and a cucumber feature.  We will add the tests to Jenkins too , so our (hypothetical) colleagues have the assurance that we're ready to release our code at any time.  Later we'll add more Cucumber features to prove that the the code continues to work, after it's deployed.

* 0:61 - 00:70  (Test Run)time *

Up until know, we've only tested each part individually. Therefore we'll deploy the application to the virtual machine that we prepared earlier, using Vlad the Deployer.  We'll update Nagios to start running the Cucumber tests that we made when we wrote the application, so the operations department can have assurance that the code is doing what it should. 

- This will show how the build pipelines of each part come together as one.
- How the test build a global artifact (from both application and operating system)
- Automation without testing is suicide

* 00:71 - 00:80 (Production Run)time in the cloud *

And finally, it's time to deliver some /real/ value! We take all this stuff and put it to good use:  We'll demonstrate that with some tiny configuration changes, we can deploy the same operating system configurations and the same application on a brand-new cloud infrastructure.  You want DR?  We have DR!

Repeating the same installation for N machines in the cloud is a breeze now!

- If it's hard do it more often
- Software doesn't bring value until it's deployed in production

* 00:81 - 00:90 Wrap-up *

Contingency, recap and questions.


_References :_

- [http://www.slideshare.net/jedi4ever/hudson-hit-puppet-with-a-cucumber](http://www.slideshare.net/jedi4ever/hudson-hit-puppet-with-a-cucumber)
- [http://www.agileweboperations.com/system-configurations-code-revisions-continuous-integration-ftw](http://www.agileweboperations.com/system-configurations-code-revisions-continuous-integration-ftw)
-
[http://www.slideshare.net/jedi4ever/continuous-integration-for-the-world-keynote-final](http://www.slideshare.net/jedi4ever/continuous-integration-for-the-world-keynote-final)
-
[http://www.slideshare.net/jedi4ever/devops-the-war-is-over-if-you-want-it](http://www.slideshare.net/jedi4ever/devops-the-war-is-over-if-you-want-it)
from slide 54

