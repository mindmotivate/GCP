# GCP Virtual Private Cloud Lab

# Lab 1 – Default VPC

## Setup
- Create a new project or select an existing project.
- Optionally, create an organization and location.

## Creating Default VPC
1. Navigate to **VPC networks**.
2. Click **Create**.
3. Enable Compute Engine when prompted.
4. Explore the default VPC and its subnets under the **Networks** tab.
   
   ![Default VPC Subnets](https://github.com/mindmotivate/GCP/assets/130941970/f8d8279b-217d-48db-b84f-29866050a05b){50%}

**Note:** If VPC creation is not complete, navigate to the **Network Interfaces** tab. Select **Network** to see the default option. Remember, in production environments, avoid using the default VPC.

## Firewall Rules
- Check the **Firewall Rules** tab.
- Auto-created rules should be present.
  
  ![Firewall Rules](https://github.com/mindmotivate/GCP/assets/130941970/fb2bfb39-d0c0-4a04-81b7-bf5bafe38388){50%}

---

# Lab 2 – Auto Mode VPC

## Setup
- Use the same project as the previous lab.

## Creating Auto Mode VPC
1. Navigate to **VPC networks**.
2. Select **Automatic**.
3. Take note of the created subnets and their respective gateway IPs.
   ![Auto Mode VPC Subnets](https://github.com/mindmotivate/GCP/assets/130941970/3192796d-1197-47b1-b7bf-35da9e3ec560){50%}
4. Check all the firewall boxes.
   ![Firewall Rules Checkbox](https://github.com/mindmotivate/GCP/assets/130941970/14cf7039-1d57-4a2a-babb-36f0e05fabca){50%}
5. Click **Create**.
   ![Create Button](https://github.com/mindmotivate/GCP/assets/130941970/941e5e65-b0ef-4aec-b0f4-1344a8d1855c){50%}

---

# Lab 3 – Custom Mode VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.

## Custom Mode VPC

### Creating Custom VPC
1. Select **Create VPC Network**.
   ![Create Custom VPC](https://github.com/mindmotivate/GCP/assets/130941970/f9c02c71-6668-4f0c-a829-8a8baaf3b46e){50%}
2. Name: "custom-vpc".
3. Choose **custom** for creation mode for subnets.

### Additional Steps
- Add subnets manually as per requirements.

### VM Creation

#### Default VM Creation
- Region: US Central 1.
- Zone: US Central 1a.
- Series: n1.
- Machine type: S1 small.
- Note the available networks: Default, Subnet, and Custom.

#### Additional VM Creation
- Create another VM with the "create similar" option.
- Note the assigned internal IP addresses.

---

# Firewall Rules Lab

## Firewall Rules Summary
- Default Rules:
  - Outgoing Traffic: Allow all outgoing traffic.
  - Incoming Traffic: Deny all incoming traffic by default.
  
## Implicit Internal Firewall Rules
- Allow All Internal Traffic
- Deny All External Traffic

## Rule Priority
- Rule Priority Range: 0-65535

## Common Ports and Protocols
- Common Ports: HTTP, SSH, RDP, ICMP

### SSH into Your Default Instance
## SSH into your default instance:
![SSH into Default Instance](https://github.com/mindmotivate/GCP/assets/130941970/f3782771-c812-448c-8ac5-b8bee8f938d5)

![SSH into Default Instance](https://github.com/mindmotivate/GCP/assets/130941970/936de153-a4fc-417d-83ec-184eefd2a74d)

# The custom VPC DOES NOT ALLOW SSH ACCESS
![Custom VPC SSH Denied](https://github.com/mindmotivate/GCP/assets/130941970/b089d1d6-1448-491b-91c9-1f16966eb887)

## Here's why:
![Custom VPC SSH Denied Explanation](https://github.com/mindmotivate/GCP/assets/130941970/9f56b5ad-f107-444a-8d44-9459effd5018)

### The firewall rules of the default VPC allow SSH
![Default VPC Firewall Rules Allow SSH](https://github.com/mindmotivate/GCP/assets/130941970/6d83919a-1173-40b4-ba99-6bf7c7e15775)

![Default VPC Firewall Rules Allow SSH](https://github.com/mindmotivate/GCP/assets/130941970/47011ff0-0732-49cb-ab06-59e0a7f90253)

### To address the problem, let's add a firewall rule to the custom VPC
![Add Firewall Rule to Custom VPC](https://github.com/mindmotivate/GCP/assets/130941970/ecf58e24-a11f-4ae3-ab0f-e97bd7e9ef2f)

### We will add an ingress rule with higher priority than 65535 (we will call it "allow-ssh")
![Add Ingress Rule for SSH](https://github.com/mindmotivate/GCP/assets/130941970/490e6372-2b7f-4235-bc72-184c5347544d)

### Don't forget to apply it to all instances in the network
![Apply Rule to All Instances](https://github.com/mindmotivate/GCP/assets/130941970/70cc02d4-89df-442d-8dc9-23e1fb381480)

### If we'd like to customize these firewall rules a bit
In this custom rule, we will:
- Create a source filter to allow the entire internet to access the instance (NOT A GOOD IDEA!)
- Create a second source filter to allow SSH traffic via TCP 
![Customize Firewall Rules](https://github.com/mindmotivate/GCP/assets/130941970/56279ddc-697c-4115-8b40-52322ce7015b)

Click "Create"

Here is our new firewall rule:
![New Firewall Rule](https://github.com/mindmotivate/GCP/assets/130941970/2bd72bdc-7fee-4d23-9176-bc80c51bb2c4)

Let's see if we can access our custom VM now via SSH?

## Success!!
![SSH Access to Custom VM](https://github.com/mindmotivate/GCP/assets/130941970/0ac69588-e317-499d-95a3-34ccfc53ee37)

---

# Creating a New Project and Default VPC Network in GCP with gcloud cli

Outline the steps for creating a new project and default VPC using gcloud commands.

---

# Creating a New Project and Default VPC Network in Terraform

Provide Terraform code for creating a project and default VPC network.
