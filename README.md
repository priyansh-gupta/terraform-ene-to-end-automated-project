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
