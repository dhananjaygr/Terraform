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
      
      1. Required .tf Files
      
      Make sure you have the following four Terraform files:
          version.tf
          main.tf
          variables.tf
          outputs.tf
      
      Steps:
          Compress all four files into a .zip folder.
          Upload the .zip file to a Storage account.
          Copy the public URL and paste it into the Cloud Template URL field in CloudLabs.
      
      2. Mandatory Variables in variables.tf
      
      Your variables.tf file must include the following mandatory variables:
          azure\_client\_id
          azure\_client\_secret
          azure\_subscription\_id
          azure\_tenant\_id
          location
      
      3. Create a .tfvars File
      
      Create a .tfvars file to define values for all variables declared in variables.tf.
          Example:
          azure\_client\_id       = "GET-SUBSCRIPTION-CLIENT-ID"
          azure\_client\_secret   = "GET-SUBSCRIPTION-CLIENT-SECRET"
          azure\_subscription\_id = "GET-SUBSCRIPTION-GUID"
          azure\_tenant\_id       = "GET-TENANT-GUID"
          location              = "eastus"
      
      # Common or Optional Variable
          DID = "GET-DEPLOYMENT-ID"
      
      Notes
      Note 1:
      
      * All mandatory variables must be present in both variables.tf and .tfvars.
      * Any variable without a default value in variables.tf must be provided in .tfvars.
      * Even if a variable has a default value in variables.tf, you can still override it in .tfvars.
      
      Note 2:
      
      * If multiple regions are selected in CloudLabs and one region already has a running deployment, new deployments will automatically shift to another available region.
      * Important: Terraform always deploys to the region specified in .tfvars.
      * To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs.
      
      Example:
      If .tfvars specifies:
      location = "us-central1"
      Then select us-central1 in CloudLabs as well.


#### Prerequisites (AWS) 


#### Prerequisites (GCP) 
