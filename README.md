# nqs-blog
Wordpress blog for AWS Certification practice

I found out a few years ago that Wordpress is a pretty good web application for learning and experimenting with AWS.<br/>
It's pretty well documented so that I've been able figure things out and troubleshoot without much effort. Since it's designed to be <br/>
used by folks with a low-level of technical knowledge, I can dedicate my time and effort to learning AWS and not Wordpress/PHP/Etc...<br/>
<br/>
It's also sufficiently complex enough that I can use a number of AWS services to build it.<br/>
For instance, if I move the database off the webserver and onto AWS RDS, I can then use AWS AutoScaling and Elastic Load Balancing to <br/>
create 3-tier (Load-balancer, Application, Database) blog that can not only scale up and down in response to traffic. Perhaps even <br/>
more important is that by moving the database off of the application server, I've ensured that if my application server dies for some <br/>
reason, my data persists on RDS. I only need to spin up another instance, install Apache/PHP/WordPress, and edit the configuration files.
<br/>
<br/>
Those last steps can be handled by a custom AMI (Amazon Machine Image) which has the software already installed and configured, or I can <br/>
do it using install scripts that run when a new EC2 instance is spun up.<br/>
<br/>
<br/>
For anyone reading this, you may wonder why I go through things a certain way. You may see me host the blog on EC2 instances and then<br/>
migrate to docker containers and wonder why not just go straight to containerization. I'm doing this as an exploration of the tech<br/>
and like to keep my notes for future reference. Sometimes I find it handy when looking back to see my understanding and process at<br/>
the time. Every time I've done this experiment with Wordpress, I've taken it from a single server hosting everything and grown it<br/>
out according to what I think would be the next logical step.<br/>
<br/>
Alright, there's one exception, I've never started it out with a database on the instance and migrated the data over to RDS because<br/>
it's pretty simple to start out with RDS and configure WP to use it.
