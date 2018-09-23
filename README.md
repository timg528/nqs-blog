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
