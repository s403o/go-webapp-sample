## Deploying with MultiStage Pipeline using Jenkins

### Prerequisites
- You will need to install SSH Build Agents and Pipeline plugins.
- You will need to add credentials and will need to add dev and prod nodes.
- In your pipeline script, you can set the default agent to none and can set the agent configuration for each stage like:
```
pipeline {
    agent none
    stages {
        agent {
            label {
                label 'dev'
                customWorkspace "/opt/go-app"
              }
        }
---
---
```

### Solution steps
#### Install Plugins:
- Go to Manage Jenkins.
- Click on Manage Plugins.
- Under Available, search for SSH Build Agents plugin and select it.
- Now search for Pipeline plugin and select it.
- Now install these plugins.
- Once installed click on Restart Jenkins when installation is complete and no jobs are running.

#### Add Credentials:
- Go to Manage Jenkins.
- Click on Manage Credentials.
- Click on (global) under Domains.
- From the options on the left side, click on Add Credentials.
- Enter Username.
- Enter Password.
- Leave other options as it is and click on OK.

#### Add Nodes:
- Go to Manage Jenkins.
- Click on Manage Nodes and Clouds.
- From the options available on the left side, click on New Node.
- Enter the Node name.
- Enable Permanent Agent option and click on OK.
- Enter Remote root directory.
- Enter Labele name.
- Select Launch Agents via SSH under Launch method.
- Enter Host and select the credentials you created.
- Under Host Key Verification Strategy, select Non verifying verification strategy.
- Leave all other options as it is and click on Save
- Click on the dev node and there shouldn't be any errors.
- Just in case the dev node is in error state, then try to relaunch it.
- Follow same steps for adding another node.

#### Create and Configure the job:
- On the left of the Jenkins dashboard, click on New Item.
- Enter the job name.
- Select Pipeline job and click on OK.
- Under Pipeline section keep selected Pipeline script as Definition
