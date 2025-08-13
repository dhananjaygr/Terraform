## 45. Terraform support for Nested files. 

### Feature Requirement

Terraform support for Nested files. 

### Implementation

In the cloudlabs template, a Zip file of nested Terraform files can be provided.

### Steps to Test the Terraform support for Nested files. 

### Prerequisites

Some prerequisites need to be followed for all the clouds (Azure, AWS, and GCP) before deploying the Nested Terraform files

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
    azure_client_id </br>
    azure_client_secret </br>
    azure_subscription_id </br>
    azure_tenant_id </br>
    location </br>
      
3. **Create a seperate .tfvars File** </br>
   Please create a .tfvars file and define values for all variables declared in your variables.tf file, including both the mandatory variables listed earlier and any additional variables required according to your deployment. </br>

   Example: </br>
   azure_client_id       = "GET-SUBSCRIPTION-CLIENT-ID" </br>
   azure_client_secret   = "GET-SUBSCRIPTION-CLIENT-SECRET" </br>
   azure_subscription_id = "GET-SUBSCRIPTION-GUID" </br>
   azure_tenant_id       = "GET-TENANT-GUID" </br>
   location              = "eastus" </br>
      
   Common or Optional Variable  </br>
   DID = "GET-DEPLOYMENT-ID" </br>
   
      
   >**Note 1:** </br>
   All mandatory variables must be present in both variables.tf file and the .tfvars file. </br>
   Any variable without a default value in variables.tf must be provided in the .tfvars file. </br>
   Even if a variable has a default value in variables.tf, you can still override it in the .tfvars. </br>
      
   >**Note 2:** </br> 
   If multiple regions are selected in CloudLabs and one region already has a running deployment, new deployments will automatically shift to another available region. </br>
   Important: Terraform always deploys to the region specified in the .tfvars file. </br>
   To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs. </br>
      
   For Example, If .tfvars specifies location = "us-central1" </br>
   Then select us-central1 in CloudLabs as well. </br>

   **Below are sample nested Terraform files for Azure:** </br>
   **Cloud Template URL:** 
   https://experienceazure.blob.core.windows.net/templates/WIZ/Testing/main.zip </br>

   **Parameter Template URL:** 
   https://experienceazure.blob.core.windows.net/templates/WIZ/Testing/cl_variablesfile_1.tfvars </br>
 
#### Prerequisites (AWS) 

Pre-requisites for Deploying AWS Terraform Files in CloudLabs
      
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
    aws_access_key </br>
    aws_secret_key </br>
    aws_region </br>
       
3. **Create a seperate .tfvars File** </br>
   Please create a .tfvars file and define values for all variables declared in your variables.tf file, including both the mandatory variables listed earlier and any additional variables required according to your deployment. </br>

   **Example:** </br>
   aws_access_key = "GET-SUBSCRIPTION-CLIENT-ID" </br> 
   aws_secret_key = "GET-SUBSCRIPTION-CLIENT-SECRET" 
   aws_region = "us-east-1"
      
   Common or Optional Variable </br>
   DID = "GET-DEPLOYMENT-ID" </br>
   
      
   >**Note 1:** </br>
   All mandatory variables must be present in both variables.tf file and the .tfvars file. </br>
   Any variable without a default value in variables.tf must be provided in the .tfvars file. </br>
   Even if a variable has a default value in variables.tf, you can still override it in the .tfvars. </br>
      
   >**Note 2:** </br> 
   If multiple regions are selected in CloudLabs and one region already has a running deployment, new deployments will automatically shift to another available region. </br>
   Important: Terraform always deploys to the region specified in the .tfvars file. </br>
   To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs. </br>
      
   For Example, If .tfvars specifies location = "us-central1" </br>
   Then select us-central1 in CloudLabs as well. </br>
       
   **Allowed Regions (AWS) in CloudLabs:** </br>
   us-east-1 </br>
   us-west-2 </br>
   us-east-2 </br>
   eu-central-1 </br>
   eu-west-1 </br>
   ap-southeast-1 </br>
   ap-southeast-2 </br>

   **Below are sample nested Terraform files for AWS:** </br>
   **Cloud Template URL:** 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/AWSTerraform/main.zip </br>

   **Parameter Template URL:** 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/AWSTerraform/wiz_variables_1.tfvars </br>


#### Prerequisites (GCP) 
