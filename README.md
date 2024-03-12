The first step while trying to complete this project was to understand the project objectives , expected outcomes and briefly the high-level required steps

**Task 1.1 initialise git repository**

- The first step in setting up Git on your local machine is to ensure that Git is installed. For Linux/Unix operating systems, you can use the following command:#sudo apt install git
- This command installs Git on your machine, making it available for use. Once Git is installed, the next step is to initialize Git in the desired directory. Make sure you are in the right directory where you want to set up your Git repository.
- To create a new directory, you can use the "mkdir" command followed by the desired folder name
- After creating the directory, navigate into it using the "cd" command
- Now that you we are in the correct directory, it's time to initialize Git. Use the following command to initialize a new Git repository "git init" This command initializes Git in the current directory, setting it up for version control. From this point onward, you can start adding files, making commits, and utilizing Git for tracking changes in your project

**Task 1.2 Obtain and prepare the E-commerce Website Template**

- This tasks is to enable us to download a ready made website template that can be tailored for us and hosted on the webserver, This will serve as our product ( where the changes will be made)
- To initiate this process, I navigated to the website provided, specifically tooplate.com, and proceeded to download the template that best suited the project's requirements. Since I lack proficiency in HTML, I opted not to make any alterations to the template and utilized it in its original form
  
  
**Task 1.3 Stage and Commit the template to git**
  
- To integrate the newly downloaded website template into Git, a series of steps were undertaken. Firstly, the file needed to be uploaded to the designated folder, which in this case is "MarketPeak_Ecommerce." Once the template was added to the required folder, the following Git commands were executed
- Adding the Template to Git:To include the downloaded website template in the Git repository, the command git add . was utilized. This command signifies the addition of all content in the current folder to Git, effectively incorporating the template into version control.
- To ensure effective tracking, reporting, and auditing, it is crucial to configure the username and user email associated with the Git commits. I used the command "git config --global user.name" and "git config --global user.email"
- Making the First Commit: Following the configuration, the initial commit was performed using the command git commit -m "comment". This command captures a snapshot of the changes made, with the comment providing context and information about the nature of the commit.
- Pushing Changes to the Main Repository:The aforementioned configurations and changes were local adjustments on the machine. To synchronize these changes with the central repository, the command git push -u origin main was executed. This command uploads the committed changes to the "main" branch on the central repository, ensuring that the central repository reflects the latest updates made locally.

**Challenge**: 
Upon executing the command git push -u origin main, an error was encountered indicating a discrepancy between the default branch names on the local machine and GitHub. The error message revealed that the default branch on the local Git repository was set to "master," while the corresponding branch on GitHub was named "main."

- Check Local Branch Name:Verify the name of the default branch on the local machine using the command:git branch
- Rename Local Branch: Rename the local branch from "master" to "main" using the following commands:git branch -m master main
- Update the local branch reference to align with the central branch name.

**AWS Deployment**

The process of creating an AWS instance is crucial for hosting a website on the server provided by AWS. Here are the steps I took to achieve this:
Logging into AWS Account: To initiate the creation of the AWS instance, I first logged into AWS account. This involves accessing the AWS Management Console.
Launching an EC2 Instance: After logging in, I proceeded to launch an EC2 instance. This involves selecting the desired AMI, specifying instance details such as type and size, configuring security groups, and defining key pairs for secure access.
Configuring Inbound Traffic Rules: During the EC2 instance launch, I configured the security groups to allow specific types of inbound traffic. I opened ports for HTTP (typically port 80), HTTPS (typically port 443), and SSH (typically port 22). This ensures that the website can handle web traffic securely and that I have SSH access to manage the instance
Connecting to the Instance via SSH.
After the instance was successfully launched, I connected to it via SSH using the key pair downloaded from AWS during the instance creation process. 

**2.2 Clone the repository on the linux server**

- For AWS to host and to be able to adapt all changes that will happen on git , it was essestial to clone git on the instance
- using the command "git clone" following by the ssh address copied from github , I successfully created a copy of the repository on ec2 instance
  
**2.3 Install a web server on Ec2**
  
  - To host the website on ec2 , i used apache http server , widely known for site hosting
  - following the steps in the note , I was installed httpd , start and enable httpd to host the downloaded website template on ec2 instance

**2.4 Configure httpd for website**
    
- To host using apache on to host the website , it is important to point the httpd to the directory where the website template is hosted
- using the command sudo cp ~/MarketPeak_Ecommerce/* /var/www/html/ which means copying the files from the directory to the httpd stucture . This will allow httpd to be able to host this website.
- Once this was successful , next step was to test that the website hosted can be accessed
- To achieve this , the public IP / template name should be copied to the browser and it should display the downloaded template
- Challenge : I kept hitting the "open address" icon with the public IP and was unable to connect. To resolve this , I copied the public IP and pasted on the web tab instead

**Continuous Integration and Deployment workflow**
- I exited the ec2 terminal
- Created a new branch on the remote repo named development 
- Switched my branch to developement 
- Made a minor change on the html file 
- Added the change to my remote branch
- Commited my changes with comment 
- Pushed the changes to git hub - origin 
- Switched back to main branch
- Merged the development branch with the main
- Pushed the changes back to the origin
- For the changes to be pull into the product environment 
- I reconnected back to the ec2 instance using ssh
- Pulled the changes using git pull origin main
- Reloaded my apache
- Then tested the changes 
- It works again!
- End 
