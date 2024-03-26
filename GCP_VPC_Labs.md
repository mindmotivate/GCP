# Lab 1 – Default VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.
![image](https://github.com/mindmotivate/GCP/assets/130941970/7c9d5aba-8d77-4362-a80b-9340cf4e2915)


***Note: The Compute Engine API needs to be enabled for each individual Google Cloud Platform (GCP)*** 
***project where you intend to use its functionalities. It's not a global setting that applies to all projects by default.***
***you would not be able to create a vm instance if there was no default vpc which is why the api creates one upon executing the compute engine*** 
![image](https://github.com/mindmotivate/GCP/assets/130941970/e2b31199-b0a0-43a3-882b-0043abb011d9)

```gcp
# enable gcp API
gcloud services enable compute.googleapis.com
```
## Creating Default VPC
1. Navigate to **VPC networks**.
   
3. Click **Create**.
4. Enable Compute Engine when prompted.
5. Explore the default VPC and its subnets under the **Networks** tab.
![image](https://github.com/mindmotivate/GCP/assets/130941970/f8d8279b-217d-48db-b84f-29866050a05b)
![image](https://github.com/mindmotivate/GCP/assets/130941970/8e79908f-b180-484b-9a8a-b4c7c9cccf8a)

Ther are 47 subnets created!
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
3. - Take note of the created subnets and their respective gateway IPs.
![image](https://github.com/mindmotivate/GCP/assets/130941970/3192796d-1197-47b1-b7bf-35da9e3ec560)

4.check all the firewall boxes
5.![image](https://github.com/mindmotivate/GCP/assets/130941970/14cf7039-1d57-4a2a-babb-36f0e05fabca)

4. Click **Create**
![image](https://github.com/mindmotivate/GCP/assets/130941970/941e5e65-b0ef-4aec-b0f4-1344a8d1855c)

### Sucessful creation
![image](https://github.com/mindmotivate/GCP/assets/130941970/5e582808-3ab1-49aa-982b-e5e0a73ba685)


6. .
7. Automatic creation results in one subnet per region and predefined firewall rules.
![image](https://github.com/mindmotivate/GCP/assets/130941970/51f04202-9a8f-46a6-a8a0-480bc92973d5)
![image](https://github.com/mindmotivate/GCP/assets/130941970/fdd1565c-5f88-4cd5-9a16-8cb53a82e5a7)
![image](https://github.com/mindmotivate/GCP/assets/130941970/4fb50874-818e-42bd-8956-1706a2fbadfc)

### Notes:

-Take note of the firewall rules
![image](https://github.com/mindmotivate/GCP/assets/130941970/5e23195e-379c-475d-a627-f6052cf910a2)



---

# Lab 3 – Custom Mode VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.

## Custom Mode VPC

### Creating Custom VPC
1. Select **Create VPC Network**.
![image](https://github.com/mindmotivate/GCP/assets/130941970/f9c02c71-6668-4f0c-a829-8a8baaf3b46e)

![image](https://github.com/mindmotivate/GCP/assets/130941970/ce4cbd07-9e80-4f3b-90a5-8b304e52df4e)

2. Name: "custom-vpc".
3. Choose **customm** for creation Mode for subnets.
4. Manually fill in subnet details.
# add a subnet called: 
![image](https://github.com/mindmotivate/GCP/assets/130941970/cf001f4a-2b11-428f-9bcd-44173f753f27)
![image](https://github.com/mindmotivate/GCP/assets/130941970/48a8a5d7-5078-49e3-ac2a-c06291cbdc81)
# create the custom vpc
name: subnet-us
![image](https://github.com/mindmotivate/GCP/assets/130941970/93183d4c-4920-4c06-8360-f226d9cd2248)



### Adding Subnet
1. Add another subnet with a non-overlapping IP range.
![image](https://github.com/mindmotivate/GCP/assets/130941970/f81cea3e-a414-40ad-b6d9-eebceb0ab563)

#notice how gcp alarms you if your ip range overlaps the current one
![image](https://github.com/mindmotivate/GCP/assets/130941970/07441d15-431d-4f24-9be2-1950712d7790)

#no overlapping range:
![image](https://github.com/mindmotivate/GCP/assets/130941970/62af210a-d34c-4c7f-840d-17146a60d787)

# click add
![image](https://github.com/mindmotivate/GCP/assets/130941970/8b61ab0a-1158-411f-a5bf-cb4c40affbbd)

## VM Creation

### Default VM Creation
1. Region: US Central 1.
2. Zone: US Central 1a.
3. Series: n1.
4. Machine type: S1 small.
5. Note the available networks: Default, Subnet, and Custom.
![image](https://github.com/mindmotivate/GCP/assets/130941970/8b6cd82a-9b2d-42d2-9c1d-d000ba6bc3dc)
![image](https://github.com/mindmotivate/GCP/assets/130941970/7266ba63-ef07-45be-acce-47605cccffa3)
![image](https://github.com/mindmotivate/GCP/assets/130941970/997cc931-45e9-4963-a133-ed862836cc19)
![image](https://github.com/mindmotivate/GCP/assets/130941970/1105fc0c-335b-4af3-b9fe-97067ef74621)

### Notes:
- the VM will be assigned an IP address from this CIDR range:
Default: 10.128.0.0/20

### Create VM
![image](https://github.com/mindmotivate/GCP/assets/130941970/91108672-06ce-4665-818b-8180ab7ce4b0)



### Additional VM Creation
1. Create another VM with the "create similar" option.
2. Note the assigned internal IP addresses.
![image](https://github.com/mindmotivate/GCP/assets/130941970/29081f86-d454-4d35-bd1f-051a86fa5296)

# use same networking defaults as previous instance
![image](https://github.com/mindmotivate/GCP/assets/130941970/c2dbc2d9-926b-4d17-bfb6-49b37d16c32e)

![image](https://github.com/mindmotivate/GCP/assets/130941970/50feb653-0f56-4b04-8078-bac63d249db5)

# create instance
notice the sequential ip address created for the instance
![image](https://github.com/mindmotivate/GCP/assets/130941970/05848df1-ec9f-41a6-877b-d6255a90c2c6)


# note: stop these instances so you wont get charged or delete if you no lnger need them!!!















# Create a a custom vm

# you may use the same subnets and vms from the previous lab if you would like however we will neeed t oadd anohter vm this one wil lbe called "auto-vm"

![image](https://github.com/mindmotivate/GCP/assets/130941970/86faef38-113a-468a-9e2a-844f12c4c2b3)
![image](https://github.com/mindmotivate/GCP/assets/130941970/7275cbd2-abc3-4771-8f97-56ab91b8c1e5)
# be sure to choose auto for "edit network interface"
![image](https://github.com/mindmotivate/GCP/assets/130941970/a1b08e96-7c8a-4e63-bc64-e1984abb93e8)
# click done
# click create


# create another instance called "custom-vm" and choose custom-vpc

![image](https://github.com/mindmotivate/GCP/assets/130941970/16cb78c8-02cc-4a10-b9cb-890f3cb984f5)
![image](https://github.com/mindmotivate/GCP/assets/130941970/1f26af6f-1c48-4f5b-9b01-31d391a2b0a9)
![image](https://github.com/mindmotivate/GCP/assets/130941970/3f199610-50f9-4ed7-9f26-823a33aeb5bb)

# try to click done

note: if you chose another region other than the region wher eyou have creaetd your subnets, you will ge tthis error: 
![image](https://github.com/mindmotivate/GCP/assets/130941970/2f521f0f-2788-4258-993a-f80811ae4f9d)

# create your custom vm
notice how the created vm ha a differnt cidr rage than the other two vms

![image](https://github.com/mindmotivate/GCP/assets/130941970/25d87e14-721b-4402-818f-47fe1c5c4168)

***note: Custom VPC Configuration: Custom VPCs allow you to define your own network configuration, 
including the CIDR block. This means you can specify the range of IP addresses that will be available 
for use within your VPC. The CIDR range chosen for the VPC might be different from the default 
CIDR range used by other services or resources.***


## Firewall Rules Lab
# Firewall Rules Summary

## Default Rules:
- **Outgoing Traffic:** Trust nothing by default.
  - Default Rule: Allow all outgoing traffic.
- **Incoming Traffic:** Deny all incoming traffic by default.


### Implicit Internal Firewall Rules

Implicit internal firewall rules are default rules that govern communication within a network:

- **Allow All Internal Traffic:** By default, communication between network resources is permitted.
- **Deny All External Traffic:** Incoming traffic from external sources is blocked by default.

These rules provide basic security within the network, allowing internal communication while restricting external access.
They have low prioty 

# Firewall riuels menu item:
![image](https://github.com/mindmotivate/GCP/assets/130941970/b890b6ed-6237-4f12-a4da-975ccf02daa9)
notice how th rulle are created for the "auto-vpc" (4)  and the "default-vpc" (6)


## Rule Priority
- Rule Priority Range: 0-65535
  - The lower the number, the higher the priority.

## Common Ports and Protocols
- **Common Ports:**
  - Port 80: HTTP
  - Port 22: SSH
  - Port 3389: RDP
  - Ping: ICMP Protocol


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




## SSH into your default instance:
![image](https://github.com/mindmotivate/GCP/assets/130941970/f3782771-c812-448c-8ac5-b8bee8f938d5)

![image](https://github.com/mindmotivate/GCP/assets/130941970/936de153-a4fc-417d-83ec-184eefd2a74d)


#  tHE CUSOMT VPC DOES NOT ALLOW ssh ACCESS
![image](https://github.com/mindmotivate/GCP/assets/130941970/b089d1d6-1448-491b-91c9-1f16966eb887)
# Here's why
![image](https://github.com/mindmotivate/GCP/assets/130941970/9f56b5ad-f107-444a-8d44-9459effd5018)


### The fire wall rules of rthe default vpc allow SSH
![image](https://github.com/mindmotivate/GCP/assets/130941970/6d83919a-1173-40b4-ba99-6bf7c7e15775)

![image](https://github.com/mindmotivate/GCP/assets/130941970/47011ff0-0732-49cb-ab06-59e0a7f90253)



### To address the problem , lets add a fire wall rule to the custom vpc
![image](https://github.com/mindmotivate/GCP/assets/130941970/ecf58e24-a11f-4ae3-ab0f-e97bd7e9ef2f)

### wew ill add an ingress rule that is higher priorty than 65535 (we will call it "allow-ssh""

![image](https://github.com/mindmotivate/GCP/assets/130941970/490e6372-2b7f-4235-bc72-184c5347544d)

### dont forget ot apply it to all intances in the network
![image](https://github.com/mindmotivate/GCP/assets/130941970/70cc02d4-89df-442d-8dc9-23e1fb381480)


### If wed like to cusotmize these firewal ruels a bit
In tis custom rule we will CREATEA SOURCE FILTER TO: allow the entire internet to acces sourinstancce (NOT A GOOD IDE!)
AND WE WIL CREATE ASECOND SOURCE FILTER TO ALLOW SSH TRAFFIC VIA TCP 
![image](https://github.com/mindmotivate/GCP/assets/130941970/56279ddc-697c-4115-8b40-52322ce7015b)



CLICK "cREATE"

HERE IS OUR NEW FIREWALL RULE:
![image](https://github.com/mindmotivate/GCP/assets/130941970/2bd72bdc-7fee-4d23-9176-bc80c51bb2c4)


lET SESE F WE CAN ACCESS OUR CUSTOM VM NOW VIA SSH?

##sUCCESS!!
![image](https://github.com/mindmotivate/GCP/assets/130941970/0ac69588-e317-499d-95a3-34ccfc53ee37)




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
gcloud components install config-connector

```

```bash
gcloud projects create PROJECT_NAME
```

```bash
$ gcloud projects add-iam-policy-binding vernal-maker-416701 \
  --member=serviceAccount:665443357168-compute@developer.gserviceaccount.com \
  --role=roles/servicenetworking.serviceAgent

gcloud projects add-iam-policy-binding vernal-maker-416701 \
  --member=serviceAccount:665443357168-compute@developer.gserviceaccount.com \
  --role=roles/storage.objectAdmin


$ gcloud beta resource-config bulk-export --resource-format=terraform --project=vernal-maker-416701



# Creating a New Project and Default VPC Network in Terraform

gcloud beta resource-config bulk-export --resource-format=terraform --project=vernal-maker-416701
sudo apt-get install google-cloud-cli-config-connector

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
