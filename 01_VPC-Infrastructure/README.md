The first thing I do is decide what my general networking layout will be.<br/>
Since I use a VPC (Virtual Private Cloud) to host my EC2 instances and most of my resources, that's where I start.<br/>
In this iteration (and yes, I've done this a lot and in a few different ways), I chose us-west-2 as my region and created blank VPC<br/>
with the IPv4 CIDR of 10.201.0.0/16. The CIDR I chose isn't really important, and this is the first time that I chose one so large and in<br/> the Class-A range. Normally I make VPCs in the Class-C range and use a /24 netmask and subdivide using /26-/28.<br/>
This time I just got lazy. The 201 is sufficiently 'out-there' in terms of IP address space that I won't run across it in other projects.<br/> 
<br/>
Note that with AWS, your VPC CIDRs do not need to be unique. I just aim for that because I may decide to use VPC Peering or VPNs <br/>
later on to connect various different projects.
<br/><br/>
I could just create one giant subnet (or three) in the VPC and rely on security groups to control access, but I'm a bit of a <br/>
neat-freak when it comes to my network topologies.<br/><br/>

One thing you need to remember is that in a VPC, subnets do not cross AZs (Availability-Zones). AZs can be thought of geographically <br/>
separated data-centers that when combined, form an AWS region. AZs can and do fail, so anything I build with an eye towards <br/>
durability, availability, disaster-prevention, etc. needs to use at least 2 AZs.<br/>
<br/>
Since the us-west-2 region offers me 3 AZs, I'm going to use all 3. I'm also going to use a 3-tier subnet structure across each AZ<br/>
to match the 3-tier application that I'm building - It'll give it a nice symmetry.<br/>
In each AZ, I'm going to have a Public subnet, and App subnet, and a Data subnet. Note that there aren't different types of subnets,<br/>
these are just the names I use for them to keep them separated in my head. <br/>
The public subnets will hold my Elastic Load Balancers, bastion hosts (if I decide to use them), NAT gateways, and anything else I <br/>
may need to access directly (like my starter instance).<br/>
The app subnets will hold my EC2 instances hosting the application servers and anything else that I decide to use for them, like EFS.<br/>
The data subnets will hold my RDS database and anything else related to the user-content of the blog.
