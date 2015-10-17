# Milestone 2

### Team Members
1. Kumar Utsav (kutsav)
2. Raman Preet Singh (rpsingh2)
3. Rohit Arora (rarora4)

### Description

We are using the following node js project as our target project: 
```
https://github.com/DevOps-HeadBangers/markdown-js
```
A build to this project installs all the dependencies and also runs the test cases.

### Tools Used

Jenkins Build Server

NPM Package Manager

Apache Tomcat 8 

Git

### Build Section

#### Install Jenkins 

1. Download and [install Tomcat8](http://www.liquidweb.com/kb/how-to-install-apache-tomcat-8-on-ubuntu-14-04/) on your system.

2. Download [jenkins.war](http://mirrors.jenkins-ci.org/war/latest/jenkins.war) file.

3. Place the war file in the /opt/tomcat/webapps directory.

4. Run tomcat server using bin/startup.sh file.

5. Open browser and go to [http://localhost:8080/jenkins](http://localhost:8080/jenkins) to run jenkins. 

#### Configure Jenkins

1. Go to Jenkins on the top left corner and choose Manage Jenkins -> Manage Plugins.

2. Install GitHub Plugin, Email Extension and NodeJS Plugins from there.

3. Now, go to Manage Jenkins -> Configure System -> NodeJS. Click Add NodeJS and click install automatically. This will give you a list of node versions. Choose according to the version installed on your system. Save.

4. To configure Email Extension,  go to Manage Jenkins -> Configure System -> Extended E-mail Notification. Now, enter the details based on your SMTP server. Under Triggers, choose Always to send an email on every build. Get Some Hints from [here](https://www.safaribooksonline.com/library/view/jenkins-the-definitive/9781449311155/ch04s08.html).

5. When you are done, save.

#### Create Jobs

1. Create a new job by clicking on Create New Job.

2. Provide the job name, choose freestyle project and click OK.

3. Now configure your job to add the target git project to the job by choosing Git from Source Code Management         Options and enter the git repository.

4. Under Build Environment, check the 'Provide Node & npm bin/ folder to PATH' option and choose the NodeJS            installation from the previous step.

5. If you want to have multiple jobs for multiple branches of the project, then give the branch name under the         Source Code Management for one of the branches.

6. Now, for other branches clone the previous job with a name reflecting the branch name and also provide the branch    name under the Source Code Management for the corresponding branch. 


#### Test Build

Go to the job page and click Build Now in the left pane. If, you get a blue sphere then that means the build was successful else you will get a red sphere.

#### Capabilities

