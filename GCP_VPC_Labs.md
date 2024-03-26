# Lab 1 – Default VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.
![image](https://github.com/mindmotivate/GCP/assets/130941970/7c9d5aba-8d77-4362-a80b-9340cf4e2915)


# Note: The Compute Engine API needs to be enabled for each individual Google Cloud Platform (GCP) 
# project where you intend to use its functionalities. It's not a global setting that applies to all projects by default.
![image](https://github.com/mindmotivate/GCP/assets/130941970/e2b31199-b0a0-43a3-882b-0043abb011d9)

```gcp
# enable gcp API
gcloud services enable compute.googleapis.com
```
## Creating Default VPC
1. Navigate to **VPC networks**.
2. Click **Create**.
3. Enable Compute Engine when prompted.
4. Explore the default VPC and its subnets under the **Networks** tab.
![image](https://github.com/mindmotivate/GCP/assets/130941970/f8d8279b-217d-48db-b84f-29866050a05b)

![image](https://github.com/mindmotivate/GCP/assets/130941970/a9e82470-28f7-4696-9be4-2f670c0777b3)

*if this is the first time you've ever used compute engine it may take a few moments to create. If not, the VPC may already appear
### Notes:
- If VPC creation is not complete, navigate to the **Network Interfaces** tab.
- Select **Network** to see the default option.
- Remember, in production environments, avoid using the default VPC.

## Firewall Rules
1. Check the **Firewall Rules** tab.
2. auto-created rules should be present:
    ![image](https://github.com/mindmotivate/GCP/assets/130941970/fb2bfb39-d0c0-4a04-81b7-bf5bafe38388)

### Drawbacks:
- Numerous unnecessary subnets may be present, posing security risks.

---

# Lab 2 – Auto Mode VPC

## Setup
- Use the same project as the previous lab.

## Creating Auto Mode VPC
1. Navigate to **VPC networks**.
2. Select **Automatic**.
3. Click **Create VPC Network**.
4. Automatic creation results in one subnet per region and predefined firewall rules.

### Notes:
- Take note of the created subnets and their respective gateway IPs.

---

# Lab 3 – Custom Mode VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.

## Custom Mode VPC

### Creating Custom VPC
1. Select **Create VPC Network**.
2. Name: "custom-vpc".
3. Choose **Creation Mode** for subnets.
4. Manually fill in subnet details.

### Adding Subnet
1. Add another subnet with a non-overlapping IP range.

## VM Creation

### Default VM Creation
1. Region: US Central 1.
2. Zone: US Central 1a.
3. Series: n1.
4. Machine type: S1 small.
5. Note the available networks: Default, Subnet, and Custom.

### Notes:
- Assign the VM an IP address from the CIDR range.

### Additional VM Creation
1. Create another VM with the "create similar" option.
2. Note the assigned internal IP addresses.

## Firewall Rules

### Overview
- Firewall rules act as traffic regulations for the network.
- There are implicit and explicit rules.
- Implicit rules are basic and unchangeable, while explicit rules are customizable.

### Ingress and Egress Rules
- Ingress: for incoming traffic.
- Egress: for outgoing traffic.
- Rules include priority, action, type of traffic, port, and enforcement status.

### Default Rules
- Default VPC includes rules for internal traffic, SSH, RDP, and ICMP.
- Priority of 65534.














# Creating a New Project and Default VPC Network in GCP with gcloud cli

This guide outlines the steps to create a new project and a default VPC network in Google Cloud Platform (GCP) using gcloud commands. It incorporates essential steps for authentication, API enablement, and network creation with default subnets.

## Prerequisites

- A Google Cloud account.
- The gcloud command-line tool installed and configured ([Install gcloud SDK](https://cloud.google.com/sdk/docs/install)).

## Steps

### Authentication and API Enablement (if necessary)

1. **Authenticate with gcloud:**
   ```bash
   gcloud auth login
   ```

```bash
gcloud services list --enabled
```

```bash
gcloud services enable compute.googleapis.com
```

```bash
gcloud projects create PROJECT_NAME
```

```bash
PROJECT_NUMBER=$(gcloud projects list --filter="name:PROJECT_NAME" \
  --format="value(projectNumber)")

gcloud compute networks create VPC_NAME \
  --project=$PROJECT_NUMBER \
  --regions REGION1,REGION2,...  # Replace with desired regions
```





# Creating a New Project and Default VPC Network in Terraform

```hcl

# provider.tf

provider "google" {
  version = "~> 3.0"  # Specify the version constraint for the provider
  region  = "us-central1"  # Specify the default region for resources
}


variable "project_name" {
  description = "The name of the GCP project to be created"
  type        = string
  default     = "my-project"
}

variable "region" {
  description = "The region where resources will be created (e.g., us-central1)"
  type        = string
  default     = "us-central1"
}

variable "vpc_name" {
  description = "The name of the default VPC network to be created"
  type        = string
  default     = "my-vpc"
}

variable "project_id" {
  description = "The ID of the GCP project (leave empty to auto-generate)"
  type        = string
  default     = ""
}

provider "google" {
  project = var.project_id
  region  = var.region
}

resource "google_project" "my_project" {
  name       = var.project_name
  project_id = var.project_id
}

resource "google_compute_network" "default_network" {
  name                    = var.vpc_name
  auto_create_subnetworks = true
}


```
