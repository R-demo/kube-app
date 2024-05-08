# KOPS for AWS
		○ instance in linux
		○ s3 bucket -  An S3 bucket is a fundamental storage resource provided by Amazon Web Services (AWS) within its Simple Storage Service (S3) offering. It's essentially a container for storing data objects, such as files and documents, in the cloud. S3 buckets are highly scalable, durable, and secure, making them ideal for various use cases ranging from simple file storage to hosting static websites, storing backups, serving as a content repository for applications, and much more
		○ IAM User  -  Identity and Access Management (IAM) that represents an individual or application that interacts with AWS resources. IAM users are typically associated with human users, such as administrators, developers, or other personnel who need access to AWS services and resources. However, they can also represent non-human entities like applications or services that require programmatic access to AWS.
		
		○ Route 53 -  highly scalable Domain Name System (DNS) web service. It allows you to register domain names, route internet traffic to the appropriate resources (such as Amazon EC2 instances, S3 buckets, or load balancers), and manage the domain's DNS records dynamically.
		○ goDaddy -get a domain

 install kubectl
 chmod +x ./kubectl

 mv kubectl to /usr/local/bin
 To create cluster
kops create cluster --name=kubevpro.groophy.xyz \ 
--state=s3://vprofile-kops10 --zones=us-east-1a,us-east-1b \ 
--node-count=2 --node-size=t3.small --master-size=t3.medium --dns-zone=kubevpro.groophy.xyz \ 
--node-volume-size=8 --master-volume-size=8

kops update cluster --name kubevpro.groophy.xyz --state=s3://vprofile-kops10 --yes --admin

create a volume
aws ec2 create-volume --availability-zone=us-east-1a --size=3--volume-type=gp2
#Delete the cluster
kops delete cluster --name kubevpro.groophy.xyz --state=s3://vprofile-kops10 --yes 
