# Overview

<TODO: complete this with an overview of your project>

## Project Plan
<TODO: Project Plan

* A link to a Trello board for the project
* A link to a spreadsheet that includes the original and final project plan>

## Instructions
requirement to running for this project.
<TODO>  
* Architectural Diagram (Shows how key parts of the system work)

<TODO>  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:
1. create resource group (rgtestig)
2. create VM using below rg
- Ubuntu Server 20.04 LTS - Gen2
- user: vmtesting
- pass: Halodc@55555
- disk: HDD option
- ip: 20.48.113.174
3. create App Service
- rg: rgtestig
- runtime: python3.7
- region: same as rg
- after deployed, goto Deployment Center
- chose repo
4. create Pool
- go to azure devops
- create project
- create enviroment
- 1. open cli, sign in to your vm
- 2. run script to create env
- 3. verify env
- create pool
- 0. create perconnel access token and save the PAT token.
- 1. navigate to project settings -> agent pool
- 2. add pool (self-hosted)
- 3. go to pool -> new agent
- 4. Download the agent
```shell
# Download the agent
curl -O https://vstsagentpackage.azureedge.net/agent/2.202.1/vsts-agent-linux-x64-2.202.1.tar.gz
# Create the agent
mkdir myagent && cd myagent
tar zxvf ../vsts-agent-linux-x64-2.202.1.tar.gz
# Configure the agent
./config.sh
...
Enter server URL > https://dev.azure.com/nguyenlehaison
Enter authentication type (press enter for PAT) > mespxw4wnyeyglsvzbb5mpoypbvjwevpyb6ircpxiw74qyohx4eq
...
2022-08-03 02:58:52Z: Settings Saved.
```
- 5. Verify agent pool
- create azure service Connection
- 1. Setting -> Service Connection -> new Azure resource manager -> named -> save
- 2. copy id on url
- go to project, created pipeline
```yml
variables:
  # Azure Resource Manager connection created during pipeline creation
  azureServiceConnectionId: 'c440471d-328f-4fd7-b21c-49de967ba6ec'

  # Web app name
  webAppName: 'hsonnlwebapp02'

  poolName: 'myAgentPool2'
  # Agent VM image name
  vmImageName: 'hsonnlLinuxVM'

  # Environment name
  environmentName: 'azwebappproject02'

  # Project root folder. Point to the folder containing manage.py file.
  projectRoot: $(System.DefaultWorkingDirectory)

  # Python version: 3.7
  pythonVersion: '3.7'
```
Issue:
if Achive zip error , then run
```shell
sudo apt-get -y install zip
```
to install zip on vm
* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


