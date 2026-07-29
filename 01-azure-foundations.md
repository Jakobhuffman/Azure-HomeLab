Azure Enterprise Security Lab 

Lesson 1: Azure Foudations 

Environment: 
Subscription display name - Azure subscription 1 
Subscription status - Active 
Subscription offer/type - Azure plan 
Directory or tenant name - University of Kansas 
Current credit remaining - $200
Credit expiration date - 29 days 

### Azure hierarchy 
Microsoft Entra tenant -> KU
|__ Azure subscription -> me
	|__ Resource group -> containers
		|__ Azure resource -> VMs, VNETs, etc.


### Key lesson 
The tenant controls identity 
The subscription controls billing and Azure resource governance 
Resource groups organize resources that share a purpose and lifecycle 

### Cost 
No resources were deployed during this lesson 
Expected cost: $0

### Security lesson 
Permissions should be assigned at the narrowest practical scope to reduce the blast radius of compromised accounts

2. Resource groups 

###RG's
I made 3 resource groups compute-lab, security, and network
I added tags to each rg for clarity and organization
All rgs are located in us central
You can confirm this in the Activity log it shows meta-data on creation and you can confirm. 


###Use
Able to add container to separate and hold azure services
Tags are used to organize, automation, and cost analysis broken into meta-data 
Activity log shows us what we created and meta-data on when it occurred   
region for a resource group does not mean everything in it will use the region you can switch it to a different one or keep it the same a the resource group the major factor to consider is the cost when selecting a region. 