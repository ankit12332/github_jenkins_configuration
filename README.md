# github_jenkins_configuration

1. Install IIS in the AWS

2. Install required plugins: In Jenkins, navigate to "Manage Jenkins" -> "Manage Plugins" -> "Available" tab. Search for and install the following plugins:

     GitHub Plugin
     NodeJS Plugin
     Git Plugin

3. Configure NodeJS Plugin

     Go to Jenkins Dashboard > Manage Jenkins > Global Tool Configuration > NodeJS.
     Click on the "Add NodeJS" button. Provide a name (like "nodejs") and select the NodeJS version you need. Save the changes.

4. Create New Jenkins Job

     Go to Jenkins Dashboard > New Item. Provide a name for the job, select "Freestyle project", and then click OK.

5. Configure GitHub Repository

     In the job configuration page:
     Under "Source Code Management", select "Git".
     Enter your repository URL in the "Repository URL" field.
     If your repository is private, you'll need to add your credentials.

6. Configure build triggers:

     Select the "GitHub hook trigger for GITScm polling" option under "Build Triggers." This allows Jenkins to trigger a build whenever a new commit is pushed to the repository.
     
     Payload URL: http://your-public-ip:8080/
     Content type: application/json
     Which events would you like to trigger this webhook? Select "Just the push event" or any other events you want to trigger Jenkins.

7. Configure Build Environment

     Under the "Build Environment" section, select "Provide Node & npm bin/ folder to PATH" and select the NodeJS installation you configured earlier.

8. Configure Build Step

     Navigate to your Jenkins job and click "Configure".
     Scroll down to the "Build" section.
     Click "Add build step" and select "Execute Windows batch command".  
     Write your shell commands as Windows commands in the new build step.
		
	cd your-project-folder  //this folder is going to create inside the programdata/jenkins/.jenkins/workspace/your-project-folder
	npm install
	npm test
	npm run build
