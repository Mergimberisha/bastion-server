1. Launch an instance
	- Ubuntu
	- Private subnet
	- Add a tag/Name
	- Create a new security group
	- Review and Launch the instance

2. Create another instance
	- Ubuntu
	- Public subnet
	- Add a tag/Name (BastionHost)
	- Create a new security group
	- Review and Launch the instance

3. Should have two instances, private subnet and the bastion subnet

4. You need to then scp the .pem ssh key into your bastion subnet. `scp -i ~/.ssh/{.pem key} {.pem key} ubuntu@{bastion public IP}:/home/ubuntu`

5. connect to the bastion host - ssh -i ubuntu@54.171.203. (bastion instance using the public ip)

6. Then connect to the private server

7. Go to your private key and then security groups and edit the inbound rules. Type = SSH - Source = your Bastion private ip /32. We only want connection from the bastion host.

8. go back to your instances on EC2.

9. We are now going to connect to the private server.

10. ssh ubuntu@{private ip} ip from the bastion server instance.

11. You then exit

12. Go back to your bastion instance, then click on security groups and check the inbound rules. It should have the type SSH and source My IP (Shouls automatically give you the IP)

13. Change the permissions. sudo chmod 400{your .pem key}

14. You should now be connected.