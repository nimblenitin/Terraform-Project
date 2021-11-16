# Terraform-Project

Simple project to implement terraform to provision resource on GCloud platform.

Steps-

Build Infrastructure
```

1. Create an instance on Gcloud compute engine

2. Install terraform with below link-
https://acloudguru.com/hands-on-labs/installing-and-configuring-terraform-on-a-compute-engine-instance

3. Create a GCP project and a service key.

4. Create a directory and create the main.tf file with configuration to provision a simple VPC network on GCloud. Make sure to mention the path to key and the project ID.
$ mkdir learn-terraform-gcp
$ cd learn-terraform-gcp
$ touch main.tf

5. initialise the terraform directory
$ terraform init

6. Format and validate the configuration
$ terraform fmt
$ terraform validate

7. Create infrastructure and Inspect state
$ terraform apply
$ terraform show

```

Change Infrastructure

```
1. Create a new resource- create the main.tf file

2. Run apply to create the resource
$ terraform apply

3. Modify the configuration- Add the tag in main.tf file and run apply

 resource "google_compute_instance" "vm_instance" {
   name         = "terraform-instance"
   machine_type = "f1-micro"
   tags         = ["web", "dev"]
   }
   
 $ terraform apply

The prefix ~ means that Terraform will update the resource in-place. You can apply this change now by responding yes, and Terraform will add the tags to your instance

4. Introduce destructive changes. Replace the image as below and run apply
image = "cos-cloud/cos-stable"
$ terraform apply

The prefix -/+ means that Terraform will destroy and recreate the resource,

```

Destroy Infrastructure

```

1. Run terraform destroy command
$ terraform destroy
The - prefix indicates that Terraform will destroy the instance and the network

```

Define input variables

```

1. Create a new file called variables.tf

2. In the main.tf file replace add the variables.
- credentials = file("<NAME>.json")
+ credentials = file(var.credentials_file)

- project = "<PROJECT_ID>"
- region  = "us-central1"
- zone    = "us-central1-c"
+ project = var.project
+ region  = var.region
+ zone    = var.zone

3. Create a file named terraform.tfvars with project ID and Credentials path.
project                  = "<PROJECT_ID>"
credentials_file         = "<FILE>"

4. Run terraform apply.
$ terraform apply

```
   


