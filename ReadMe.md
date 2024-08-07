AWS Webpage Deployment
-----------------------
Designed a Web application to be deployed on AWS S3 buckets and EC2 instances using HTML, CSS, Javascript, and AWS Virtual Machine.

Live Webpage: [Survey form](https://ramiyappan.github.io/AWS-Webpage-Deployment/)


PART-1: Homepage
----------------

- Created personal website of a short portfolio about myself containing picture, description and skills including links to the application using VScode.
- Created S3 bucket in the name ramiyappan-gmu.com following the listed steps @ https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html.
- Enabled static website hosting for the created bucket and mentioned index and error files.
- Added all necessary objects including HTML file `mywebsite.html`, CSS file `stylesheet.css` and other images.

>[!NOTE]
>Previously hosted @ [AWS](http://ramiyappan-gmu.com.s3-website-us-east-1.amazonaws.com/),
>currently not accessible since instances have been terminated.

PART-2:	Survey-Form
-------------------

- Created Survey Form in the Dynamic Web Project environment using Eclipse IDE.
- Installed and connected to Tomcat runtime environment and JDK packages while creating the web project in Eclipse to ensure that project have access to the local host.
- Project contains `survey.html` which is the Survey Form and `stylesheet.css` which is the external style sheet for the webpage, and other necessary images.
- Deployed application on local tomcat server @ `localhost:8080`
- Extracted the Eclipse project as a WAR file along with all the source files.
- Created and setup new EC2 instance in Amazon EC2 console using "Tomcat packaged by Bitnami" AMI, `t2.micro` free tier version and rest default settings.
- Created and downloaded new key pair `hw1.pem`.
- While creating the instance, it was ensured that the security group settings allow the instance to be publicly accessible.
- After following all the above steps, the EC2 instance was successfully created.

- Now, to deploy the extracted WAR file onto the EC2 instance, navigate to the location of the .war file `Survey.war` 
and .pem file `hw1.pem` on the local system and execute the following commands in a terminal:

	1. Change privacy of the key. 
	```
 	chmod 400 hw1.pem
 	```
	2. Connect and copy WAR file from system to EC2 instance using it's Public IPv4 DNS address.
	```
 	scp -i hw1.pem Survey.war bitnami@ec2-52-86-87-37.compute-1.amazonaws.com:~/.
 	```
	3. Connect to the instance from the terminal.
	```
 	ssh -i "hw1.pem" bitnami@ec2-52-86-87-37.compute-1.amazonaws.com
 	```
	4. Copy WAR file to tomcat server directory.
	```
	sudo cp Survey.war stack/tomcat/webapps
 	```

- Make sure that the EC2 instance and Eclipse web project are created according to the above settings so that the required access and security is established.
- The WAR file was finally deployed on the EC2 instance using its Public IPv4 DNS.

>[!NOTE]
>Previously hosted @ [AWS](https://ec2-52-86-87-37.compute-1.amazonaws.com/Survey/survey.html),
>currently not accessible since instances have been terminated.
