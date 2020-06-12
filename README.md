# terraform-ene-to-end-automated-project
1. Creating an EC2 instance.
2. Downloaded a code from github in Linux OS
3. Terraform performed ssh to EC2 machine where github code downloaded to /var/www/html.
4. There is volume created where /var/www/html is mounted to volume for persistent storage.
5. Learnt how to push Linux based command from Terraform to Linux OS.
6. Learnt to use keywork as force --detach in case complete infrastructure to be destroyed.
7. In AWS EC2 OS HDD device name is with xvdh instead of sdh.
8.Now we also need to check which command executed first and which one later which can be done using depends_on keyword which will
run command sequentially.
9. We can also create linux based OS command using Ansible and can include the same in terraform.


### high level concepts
1. we automate the entire process of establishing the cloud setup uisng Terraform which is known as #IAAC

2. if the requirement is to run the base OS command using the terraform code then Terraform provides us the #Provisioner which is run the OS commands on local system and also on remote-system. This is also called provision local command or remote command.

3. Provisioner is the part of resource keyword and it uses two keywords i) local which perform local-execution and ii) remote which perform remote-execution. We need to use keyword #null_resource as a resource type.

4. some example to use terraform for running OS commands on local windows system.

5. an example to which we need to automate entirely. For this we had performed the these jobs:
i) created a git repo and also create a php code file.
ii) launched an ec2 instance using terraform code as we have done in previous classes.
iii) then we have to install some software in the same instance so that we had used yum install command to install php, 
iv) for software installation we require to login so that we need to establish connection and for this we have used #connection which help to login into the instance via #ssh.
v) then we have attach a volume using another resource type called #aws_ebs_volume in the same region where we have created the instance
vi) then we attached volume to the instance using resource type #aws_volume_attachement after that we formatted and mounted the volume using another provisioner with keyword as #remote-exec that run mkfs.ext4 and mount command then we clone the git repo in that volume.

6. whenever we use provisioner with multiple resources then Terraform try to launch null resource first. But some time we need a sequence as all these jobs are dependent on each other so we need to provide an order of dependency in between these jobs that would be provided by #depends_on variable in resource type as null_resource.

i) if we try to destory the running instance using #terraform_destory command and some volume is attached to it then it show error like volume is busy then we need to go to the console and manually de-attach the volume form instance.

ii) if we are trying to clone the git repo in some folder and folder is not empty then git throwing an error or warning. So that we need to provide an empty folder to it.

7. in this class we have automate the all the basic thing which are required to launch a fresh webserver using a small piece of code it is little bit painful when we try to create for first time but after that it will it easy and work as a document so that we can share it to other people if the requirement are same.

8. that we automate apply and deploy by using #auto_approve option with terraform apply and destory command it necessary to automate apply and destory also otherwise it will create some issues during testing.
