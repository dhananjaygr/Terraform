## 45. Terraform support for Nested files. 

### Feature Requirement

Terraform support for Nested files. 

### Implementation

In the cloudlabs template, a Zip file of nested Terraform files can be provided.

### Steps to Test the Terraform support for Nested files. 

### Prerequisites

Some prerequisites need to be followed for all the clouds (Azure, AWS, and GCP) before deploying the Nested Terraform files

#### 1. Prerequisites (Azure) 

Pre-requisites for Deploying Azure Terraform Files in CloudLabs
      
- **Required .tf Files** </br>
   Make sure you have the following four Terraform files: </br>
   version.tf </br>
   main.tf </br>
   variables.tf </br>
   outputs.tf </br>
      
   **Steps:** </br>
   Compress all four files into a .zip folder. </br>
   Upload the .zip file to a Storage account. </br>
   Copy the public URL and paste it into the Cloud Template URL field in CloudLabs. </br>
      
- **Mandatory Variables in variables.tf** </br>
    Your variables.tf file must include the following mandatory variables: </br>
    azure_client_id </br>
    azure_client_secret </br>
    azure_subscription_id </br>
    azure_tenant_id </br>
    location </br>
      
- **Create a seperate .tfvars File** </br>
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
   **Important:** Terraform always deploys to the region specified in the .tfvars file. </br>
   To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs. </br> 
   For Example, If .tfvars specifies location = "us-central1" </br>
   Then select us-central1 in CloudLabs as well. </br>

   **Below are sample nested Terraform files for Azure:** </br>
   **Cloud Template URL:** </br> 
   https://experienceazure.blob.core.windows.net/templates/WIZ/Testing/main.zip </br>

   **Parameter Template URL:** </br> 
   https://experienceazure.blob.core.windows.net/templates/WIZ/Testing/cl_variablesfile_1.tfvars </br>
 
#### 2. Prerequisites (AWS) 

Pre-requisites for Deploying AWS Terraform Files in CloudLabs
      
- **Required .tf Files** </br>
   Make sure you have the following four Terraform files: </br>
   version.tf </br>
   main.tf </br>
   variables.tf </br>
   outputs.tf </br>
      
   **Steps:** </br>
   Compress all four files into a .zip folder. </br>
   Upload the .zip file to a Storage account. </br>
   Copy the public URL and paste it into the Cloud Template URL field in CloudLabs. </br>
      
- **Mandatory Variables in variables.tf** </br>
    Your variables.tf file must include the following mandatory variables: </br>
    aws_access_key </br>
    aws_secret_key </br>
    aws_region </br>
       
- **Create a seperate .tfvars File** </br>
   Please create a .tfvars file and define values for all variables declared in your variables.tf file, including both the mandatory variables listed earlier and any additional variables required according to your deployment. </br>

   **Example:** </br>
   aws_access_key = "GET-SUBSCRIPTION-CLIENT-ID" </br> 
   aws_secret_key = "GET-SUBSCRIPTION-CLIENT-SECRET" </br> 
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
   For Example, If .tfvars specifies location = "us-east-1" </br>
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
   **Cloud Template URL:** </br> 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/AWSTerraform/main.zip </br>

   **Parameter Template URL:** </br> 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/AWSTerraform/wiz_variables_1.tfvars </br>


#### 3. Prerequisites (GCP) 

Pre-requisites for Deploying GCP Terraform Files in CloudLabs
      
- **Required .tf Files** </br>
   Make sure you have the following four Terraform files: </br>
   version.tf </br>
   main.tf </br>
   variables.tf </br>
   outputs.tf </br>
      
   **Steps:** </br>
   Compress all four files into a .zip folder. </br>
   Upload the .zip file to a Storage account. </br>
   Copy the public URL and paste it into the Cloud Template URL field in CloudLabs. </br>
      
- **Mandatory Variables in variables.tf** </br>
    Your variables.tf file must include the following mandatory variables: </br>
    credentials_file 
    project_id 
    region 
       
- **Create a seperate .tfvars File** </br>
   Please create a .tfvars file and define values for all variables declared in your variables.tf file, including both the mandatory variables listed earlier and any additional variables required according to your deployment. </br>

   **Example:** </br>
   credentials_file = "key.json" </br> 
   project_id          = "GET-SUBSCRIPTION-FRIENDLY-NAME" </br> 
   region                 = "us-central1" </br> 
      
   Common or Optional Variable </br>
   DID = "GET-DEPLOYMENT-ID" </br>
   
   >**Note 1:** </br>
   For zonal resources, you must specify the zone value in both variables.tf file (e.g., variable "zone" {}) and the .tfvars file.   
      
   >**Note 2:** </br>
   All mandatory variables must be present in both variables.tf file and the .tfvars file. </br>
   Any variable without a default value in variables.tf must be provided in the .tfvars file. </br>
   Even if a variable has a default value in variables.tf, you can still override it in the .tfvars. </br>
      
   >**Note 3:** </br> 
   If multiple regions are selected in CloudLabs and one region already has a running deployment, new deployments will automatically shift to another available region. </br>
   Important: Terraform always deploys to the region specified in the .tfvars file. </br>
   To avoid conflicts or inconsistencies, make sure the region in .tfvars matches one of the selected regions in CloudLabs. </br> 
   For Example, If .tfvars specifies location = "us-central1" </br>
   Then select us-central1 in CloudLabs as well. </br>
       
   **Allowed Regions (GCP) in CloudLabs:** </br>
   us-east4 </br>
   us-west1 </br> 
   australia-southeast1 </br> 
   europe-west1 </br> 
   me-west1 </br> 
   asia-northeast1 </br> 
   us-central1 </br> 

   **Below are sample nested Terraform files for AWS:** </br>
   **Cloud Template URL:** </br> 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/GCPTerraform/Prod3.zip </br>

   **Parameter Template URL:** </br> 
   https://cloudlabs-prod-templates-s3.s3.us-east-1.amazonaws.com/WIZ/test/GCPTerraform/var_file_3.tfvars </br>


1. Log in to the CL portal and navigate to the required tenant (WIZ). On the left-hand side of the page, you will see the Template section.

2. Navigate to the **Template (1)** section in the left menu and go to your respective Template. Click the **Edit (2)** button.

   ![](./Img/01.png)

3. In the template, scroll down to the **Cloud Template** section. Then, either edit an existing template or click **Add** if it’s a new template.

4. Under the Cloud Template section, ensure that Template Type is set to **Terraform (1)** from the dropdown. Then, select Template File Type as **ZIP (2)**.

5. Then provide the following: </br>
   **Terraform Script URL – Paste the URL of the .zip file containing all your Terraform files. (3)** </br>
   **Parameter Template URL – Paste the URL of the .tfvars file. (4)** </br>

6. Click the **Submit (5)** button. 

   ![](./Img/02.png)

7. Finally, click the **Submit** button for the entire template.

   ![](./Img/03.png)

8. Navigate to the **ODL (1)** section in the left menu and go to your respective ODL. Click the **Users (2)** button and deploy the user.

   ![](./Img/04.png)


