The first step while trying to complete this project was to understand the project objectives , expected outcomes and briefly the high-level required steps
**Task 1.1 initialise git repository **
- The prequesite for git initialisation is to the installation of git on the local machine. To install git using this command should be used "sudo apt install git" for linux/unix operation systems
- Following the installation , to ensure git is intialised on the right directory , we need to ensure we are in the right directory. For this project , the task is to be able to create a directory on the local machine and change the directory into the newly created directorty. To create the directory , the command "mkdir" can be used following by the folder name.
- To access the newly created directory , the command "cd" following by the directory name should be used .
- To start or initialise Git , whilst in the newly created directory , the command "git init" should be used to initialise git.

**Task 1.2 Obtain and prepare the E-commerce Website Template**
- This tasks is to enable us to download a ready made website template that can be tailored for us and hosted on the webserver, This will serve as our product ( where the changes will be made)
- I naviagted to the site provided tooplate.com and download the specific template for the project. As I have no html skills , I didnt not make any amendment to the template and used as it is
**1.3 Stage and Commit the template to git **
- For the newly downloaded website template to be added to git , the file firstly needed to be uploaded onto the requried folder i.e MarketPeak_Ecommerce
- Once this was added and for me to add the website downloaded to git , I used the command "git add ." which denotes adding all content in the current folder to git i.e adding the downloaded website template to git
- For tracking and logging purposes , it is important to set up username and useremail . This especially will be useful in real life scenarios for tracking , reporting and auditing purposes. To set up user name and user email , I used the command "git config --global user.name" and "git config --global user.email"
- After configuration I made my first commit with a comment using "git commit -m" following by my comment 
- All above configuraion and changes are remote changes i.e changees made on local machine , for this changes to be uploaded on the main repository , this change will need to be pushed to origin using the command "git push -u origin main"
- **Challenge **: When I ran that command , this came back with the error notifying me that the remote branch and the one on github are different i.e the default branch on the git remote branch is "master" while the default branch on github is "main" 
- To resolve the issue , i renamed the remote default branch to main using the command "git branch -m Master Main"
- I rerun the command and my website was added on github

AWS Deployment 
The creation os AWS instance is to enable the website to be hosted on the server created on AWS
For me to create the server 
- I logged in my AWS account
- Launch an EC2 instance allowing the inbound traffic from HTTp , HTTPS and SSH
- Connected to my instance via SSH using my keypair downloaded from AWS

2.2 Clone the repository on the linux server 
- For AWS to host and to be able to adapt all changes that will happen on git , it was essestial to clone git on the instance
- using the command "git clone" following by the ssh address copied from github , I successfully created a copy of the repository on ec2 instance
  2.3 Install a web server on Ec2
  - To host the website on ec2 , i used apache http server , widely known for site hosting
  - following the steps in the note , I was installed httpd , start and enable httpd to host the downloaded website template on ec2 instance
    2.4 Configure httpd for website
- To host using apache on to host the website , it is important to point the httpd to the directory where the website template is hosted
- using the command sudo cp ~/MarketPeak_Ecommerce/* /var/www/html/ which means copying the files from the directory to the httpd stucture . This will allow httpd to be able to host this website.
- Once this was successful , next step was to test that the website hosted can be accessed
- To achieve this , the public IP / template name should be copied to the browser and it should display the downloaded template
- Challenge : I kept hitting the "open address" icon with the public IP and was unable to connect. To resolve this , I copied the public IP and pasted on the web tab instead

Continuis Integration and Deployment workflow
I exited the ec2 terminal
created a new branch on the remote repo named development 
switched my branch to developement 
made a minor change on the html file 
added the change to my remote branch
commited my changes with comment 
pushed the changes to git hub - origin 
switched back to main branch
merged the development branch with the main
pushed the changes back to the origin
For the changes to be pull into the product environment 
I reconnected back to the ec2 instance using ssh
pulled the changes using git pull origin main
reloaded my apache
then tested the changes 
It works again!
End 
