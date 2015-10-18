# Milestone 2

### Team Members
1. Kumar Utsav (kutsav)
2. Raman Preet Singh (rpsingh2)
3. Rohit Arora (rarora4)

### Description

We are using the following node js project as our target project: 
```
https://github.com/DevOps-HeadBangers/target-node-project.git
```
A build to this project installs all the dependencies and also runs the test cases.

### Tools Used

Jenkins Build Server

NPM Package Manager

Apache Tomcat 8 

Git

Tape Testing Framework

Esprima

ESLint

Istanbul

### Basic Setup

#### Install Jenkins 

1. Download and [install Tomcat8](http://www.liquidweb.com/kb/how-to-install-apache-tomcat-8-on-ubuntu-14-04/) on your system.

2. Download [jenkins.war](http://mirrors.jenkins-ci.org/war/latest/jenkins.war) file.

3. Place the war file in the /opt/tomcat/webapps directory.

4. Run tomcat server using bin/startup.sh file.

5. Open browser and go to [http://localhost:8080/jenkins](http://localhost:8080/jenkins) to run jenkins. 

#### Configure Jenkins

1. Go to Jenkins on the top left corner and choose Manage Jenkins -> Manage Plugins.

2. Install GitHub Plugin, TAP Plugin, CheckStyle Plugin, Clover Coverage Plugin and NodeJS Plugin from there.

3. Now, go to Manage Jenkins -> Configure System -> NodeJS. Click Add NodeJS and click install automatically. This will give you a list of node versions. Choose according to the version installed on your system. Save.

4. When you are done, save.

#### Create Jobs

1. Create a new job by clicking on Create New Job.

2. Provide the job name, choose freestyle project and click OK.

3. Now configure your job to add the target git project to the job by choosing Git from Source Code Management         Options and enter the git repository.

4. Under Build Environment, check the 'Provide Node & npm bin/ folder to PATH' option and choose the NodeJS            installation from the previous step.


#### Test Section

##### The ability to run unit tests, measure coverage, and report the results

1. Go to the Configure page of your job.

2. Under Build section, choose 'Execute Shell' option for Add Build Step option.

3. Add the following code to the 'Execute Shell Command'. This script will do a clean npm install, run unit tests,     measure coverage and report the results.  
    ```
    rm -rf node_modules
    npm install
    npm run ci-test || :
    ```
    
4. Under 'Post Build Sections', choose 'Publish TAP Results' for 'Add Post Build Action' option. And, for 'Test        Results' textbox, write 'test.tap'. 'test.tap' file will contain the result of ```istanbul cover test.js```.

5. Again, under 'Post Build Sections', choose 'Publish Clover Coverage Report' for 'Add Post Build Action' option.     And, for 'Clover Report Directory' textbox, write 'coverage'. 'coverage' is the folder that will contain the        istanbul coverage reports. Click 'Apply' and 'Save' when done.

Following is the screencast for the capability:

##### The ability to improve testing coverage using one of the techniques covered in class: constraint-based test generation, fuzzing, etc. You can use an existing tool or implement your own approach.

To the 'Execute Shell Command' of the previous capability, add ```node testgen.js```. Adding this command will generate new test cases and improve the test coverage. The tests are generated using constraint based test        generation. Click 'Apply' and 'Save' when done.

Following is the screencast for the capability:

#### Analysis Section

##### The ability to run an existing static analysis tool on the source code (e.g. FindBugs, PMD, CheckStyle, NCover, Lint, etc.), process its results, and report its findings.

For this capability, to the 'Execute Shell Command' of the previous capability, add ```npm run ci-lint || :```.  Under 'Post Build Sections', choose 'Publish CheckStyle Analysis Results' for 'Add Post Build Action' option. Click 'Apply' and 'Save' when done.

Following is the screencast for the capability:

##### The ability to extend an existing analysis tool with a custom analysis, or implement a new analysis from scratch. For example, you could write a static analysis that checks for the ratio of comments to code, or finds parse errors in SQL string statements. You could introduce security checks, a dynamic analysis, a data-flow analysis or a data-flow based test coverage.

For this capability, add ```node analysis.js``` to the 'Execute Shell Command' of the previous capability. Click 'Apply' and 'Save' when done. This will output the comment to code line ratio on the console output. 

Following is the screencast for the capability:

##### Using hooks or post-build scripts, have the ability to reject a commit if it fails a minimum testing criteria (e.g. failed test case, or less than 50% statement coverage) and analysis criteria (e.g. cannot commits that generate a particular FindBugs rule, such as "Method concatenates strings using + in a loop").


