## 45. Terraform support for Nested files. 

### Feature Requirement

Terraform support for Nested files. 

### Implementation

In the cloudlabs template, a Zip file of nested Terraform files can be provided.

### Steps to Test the Terraform support for Nested files. 

### Prerequisites

Some prerequisites need to be followed for all the clouds (Azure, AWS< GCP) before deploying the Nested Terraform files

#### Prerequisites (Azure) 

Pre-requisites for Deploying Azure Terraform Files in CloudLabs
      
1. **Required .tf Files** </br>
   Make sure you have the following four Terraform files: </br>
   version.tf </br>
   main.tf </br>
   variables.tf </br>
   outputs.tf </br>
      
   **Steps:** </br>
   Compress all four files into a .zip folder. </br>
   Upload the .zip file to a Storage account. </br>
   Copy the public URL and paste it into the Cloud Template URL field in CloudLabs. </br>
      
2. **Mandatory Variables in variables.tf** </br>
    Your variables.tf file must include the following mandatory variables: </br>
    azure\_client\_id </br>
    azure\_client\_secret </br>
    azure\_subscription\_id </br>
    azure\_tenant\_id </br>
    location </br>
      
3. **Create a .tfvars File** </br>
   Create a .tfvars file to define values for all variables declared in variables.tf. </br>
   Example: </br>
   azure\_client\_id       = "GET-SUBSCRIPTION-CLIENT-ID" </br>
   azure\_client\_secret   = "GET-SUBSCRIPTION-CLIENT-SECRET" </br>
   azure\_subscription\_id = "GET-SUBSCRIPTION-GUID" </br>
   azure\_tenant\_id       = "GET-TENANT-GUID" </br>
   location              = "eastus" </br>
      
   Common or Optional Variable  </br>
   DID = "GET-DEPLOYMENT-ID" </br>
      
   >**Note 1:** </br>
   All mandatory variables must be present in both variables.tf and .tfvars. </br>
   Any variable without a default value in variables.tf must be provided in .tfvars. </br>
   Even if a variable has a default value in variables.tf, you can still override it in .tfvars. </br>
      
   >**Note 2:** </br> 
   If multiple regions are selected in CloudLabs and one region already has a running deployment, new deployments will automatically shift to another available region. </br>
   Important: Terraform always deploys to the region specified in the .tfvars file. </br>
   To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs. </br>
      
   **Example:** </br>
   If .tfvars specifies: location = "us-central1" </br>
   Then select us-central1 in CloudLabs as well. </br>


#### Prerequisites (AWS) 


#### Prerequisites (GCP) 
