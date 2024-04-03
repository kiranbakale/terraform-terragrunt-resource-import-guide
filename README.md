# terraform-terragrunt-resource-import-guide

<p align="center">
  <img src ="https://img.shields.io/badge/Terraform-412991.svg?style&logo=Terraform&logoColor=white"/>
  <img src ="https://img.shields.io/badge/Terragrunt-375EAB.svg?style&logo=Terragrunt&logoColor=white"/>

Are you struggling to integrate manually created resources into your Terraform-Terragrunt management system? While importing resources into Terraform is a well-documented process, it becomes quite tricky when incorporating pre-existing resources under Terragrunt’s umbrella. Fear not! In this comprehensive guide, I'll walk you through the step-by-step process of seamlessly integrating your manually provisioned infrastructure into Terraform-Terragrunt’s fold.

---

## Steps to Integrate Manual Resources:

Begin by listing all resources currently managed by Terraform-Terragrunt:

```bash
# Step 1: Assess Your Managed Resources
terragrunt state list
```
- Similar to importing resources in Terraform, add the following snippet to any file to initiate the import process. Replace placeholders with your resource specifics:
 ```bash
import {
  to = resourcetype.resourcename
  id = "your resource id"
}
```
- Next, generate a code snippet to facilitate efficient management of the imported resource:
```bash

terragrunt plan -generate-config-out=yourdesiredfilename.tf
```
- Note that the generated configuration file won’t be found in the usual tf-files section. Navigate to the Terragrunt cache files to locate it:

```bash
.terragrunt-cache/files-located-here
```
- Copy the generated configuration file from the cache and paste it into the original tf-files location.
- Apply the changes to ensure that your infrastructure aligns with the Terraform-Terragrunt code:

```bash
terragrunt apply
```
- Confirm that your manually provisioned infrastructure now seamlessly matches the Terraform-Terragrunt code:
```bash
terragrunt state list
```

- By following these steps, you can efficiently integrate manual resources into Terraform-Terragrunt management, streamlining your infrastructure control process.







