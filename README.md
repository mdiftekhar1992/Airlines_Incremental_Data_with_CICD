# Airlines_Incremental_Data_with_CICD
Step-by-Step Documentation for CICD Process
1. Azure DevOps Setup
Create Azure DevOps Account:
Set up an account and create a new Organization.

Set Up a Project:
Within the organization, create a project to house your source code, pipelines, and related resources.

Repository Configuration:
Use GitHub or the inbuilt Azure Repos to store:

ADF ARM templates.
Scripts or configuration files (e.g., JSON pipeline files).
Agent Pool Setup:
Configure an Agent Pool in Azure DevOps to link with your local machine or hosted agent for running the pipelines.

2. Development Environment Pipeline Setup
Source: ADLS

Load incremental data files into Azure Data Lake Storage (ADLS), organizing them by folders (e.g., date, region, etc.).
ADF Pipeline Creation:

Use Azure Data Factory to create the ETL pipeline.
Define Linked Services for ADLS and Synapse Analytics.
Build data flows for:
Extracting data from ADLS.
Transforming or cleaning data.
Loading processed data into Azure Synapse Analytics.
Unit Testing:

Validate the pipeline execution in the Development environment.
3. CICD Pipeline Setup in Azure DevOps
a) Build Pipeline
Build Templates:

Create a YAML build pipeline in Azure DevOps to package ADF ARM templates.
Steps in the Build Pipeline:

Fetch code from the GitHub/Azure Repo.
Validate the ARM templates.
Archive the validated template into an artifact for deployment.
Output:

A packaged artifact ready for deployment.
b) Release Pipeline
Define Stages:

Dev: Deploy and test the pipeline.
Prod: Automatically release tested pipelines into the production environment.
Release Steps:

Use the artifact created in the build pipeline.
Deploy ARM templates to the target ADF instance.
Verify deployment.
Automation with Logic Apps:

Add a Logic App to trigger pipeline execution after successful deployment.
4. Production Deployment
Automated Deployment:

Push updates directly to Production ADF Pipeline using the Release pipeline.
Ensure Synapse Analytics stores incremental, processed data.
Monitoring:

Use Azure Monitor to track ADF pipeline executions and Logic App activity.
![diagram-export-05-12-2024-18_36_01](https://github.com/user-attachments/assets/deb0531b-a6c1-42f7-900d-a767bf3750f5)
