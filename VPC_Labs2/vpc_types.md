# Network / Cloud
A network, in its simplest form, is a collection of interconnected devices (such as computers, servers, printers, etc.) that can communicate with each other. This communication can happen within a local area (LAN), like in a home or office, or over a larger geographical area (WAN), such as connecting different office branches across a city or country.

An IP (Internet Protocol) address is a unique identifier assigned to each device connected to a computer network. It's like a digital address that helps data find its way to the right destination on the internet or within a local network.

RFC 1918 defines certain ranges of IP addresses that are reserved for private networks, which means they're not routable over the internet. These reserved ranges are:

***10.0.0.0 - 10.255.255.255***

***172.16.0.0 - 172.31.255.255***

***192.168.0.0 - 192.168.255.255***

A subnet in a VPC is a way to divide your network into smaller, manageable parts. It's defined by a CIDR (Classless Inter-Domain Routing) block, which specifies the range of IP addresses available to devices within that subnet. This helps in organizing and efficiently using IP addresses within your VPC while also providing segmentation for security and management purposes.

In Google Cloud Platform (GCP), think of a network as the foundation that connects all your resources together, like how roads connect different parts of a city. Without roads, you can't reach your destination. Similarly, without a network in GCP, your resources, like virtual machines or databases, can't communicate with each other or with the outside world.

So, when you create a resource in GCP, like a virtual machine, it needs to be part of a network to function properly. This network provides the pathways for data to travel between your resources, ensuring they can talk to each other and to the internet if needed.

# Default VPC:
**Default VPC:** When you create a project in GCP, a default VPC is automatically created for you. It's a simple setup suitable for getting started quickly. It comes with a predefined set of firewall rules that allow outbound connections and deny incoming connections, providing basic security.
- **Description**: When you create a new project in GCP, a default VPC is automatically provisioned for you. It's a ready-to-use VPC with default settings that allow you to quickly deploy resources without additional configuration.
- **Subnets**: By default, a default VPC includes one subnet in each region where resources can be deployed. These subnets are created with predefined IP ranges.
- **Firewall Policies**: Default firewall rules are automatically applied to the default VPC to allow certain types of traffic, such as SSH and RDP for remote access, and deny all other traffic by default.

# Auto Mode VPC:
**Auto Mode VPC:** This model provides more flexibility compared to the default VPC. It allows for automatic subnet creation, which means you don't have to worry about managing IP addresses manually. Google Cloud automatically creates and manages subnets for you, making it easier to scale your infrastructure.
- **Description**: Auto Mode VPC allows you to create subnets with predefined IP ranges automatically. When you create a subnet in Auto Mode, GCP automatically assigns IP addresses from a predefined range for that region.
- **Subnets**: Subnets in Auto Mode VPCs are created with predefined IP ranges based on the region. Each subnet is automatically created within the VPC when you deploy resources.
- **Firewall Policies**: Similar to Default VPC, Auto Mode VPC comes with default firewall rules applied to control incoming and outgoing traffic. These rules can be customized as needed.

# Custom Mode VPC:
**Custom Mode VPC:** This is the most flexible option, allowing you to have complete control over your VPC configuration. You can define your own IP ranges, subnets, and firewall rules to tailor the network setup according to your specific requirements. This model is suitable for complex network architectures and advanced networking scenarios.
- **Description**: Custom Mode VPC provides full control over the VPC configuration, allowing you to define custom IP ranges and subnets.
- **Subnets**: In Custom Mode VPC, you can define your own IP ranges and create subnets within those ranges. You have flexibility in defining the size and range of each subnet.
- **Firewall Policies**: Custom Mode VPC allows you to define custom firewall rules to control inbound and outbound traffic. You can create rules based on specific IP ranges, protocols, and ports, providing granular control over network traffic.


# Setting Up a Default VPC in Google Cloud Platform
## Tutorial for Setting Up Each Type of VPC:
### Default VPC:
- Simply create a new project in GCP, and the default VPC will be automatically provisioned for you. You can start deploying resources immediately without any additional setup.


## Introduction:

In this tutorial, we'll guide you through setting up a default VPC (Virtual Private Cloud) in Google Cloud Platform (GCP). A default VPC provides a pre-configured networking environment, allowing you to quickly deploy resources without the need for additional network configuration.

## Prerequisites:

- Google Cloud Platform account.
- Basic familiarity with navigating the Google Cloud Console.

## Step-by-Step Guide:

### 1. Creating a Project:

- Log in to your Google Cloud Console at https://console.cloud.google.com/.
- If you don't have a project yet, create one by clicking on the project dropdown menu at the top of the page and selecting "New Project". Follow the prompts to set up your project.
- Once your project is created, make sure it's selected in the project dropdown menu.

### 2. Activating Compute Engine API:

- In the Google Cloud Console, navigate to the main menu by clicking on the three horizontal lines in the top left corner.
- Under the "Compute" section, select "Compute Engine".
- If prompted, click on "Enable" to activate the Compute Engine API for your project.

### 3. Setting Up Default VPC:

- Once the Compute Engine API is enabled, a default VPC is automatically provisioned for your project. You don't need to take any additional steps to set it up.
- The default VPC comes with default settings that allow you to quickly deploy resources without any additional configuration.
![image](https://github.com/mindmotivate/GCP/assets/130941970/8e7c69a3-0aa9-422d-ab20-3a324e522002)

![image](https://github.com/mindmotivate/GCP/assets/130941970/4b555087-72bc-45b9-bee5-c5e7c0edec0e)

### 4. Understanding Default VPC Features:

- **Description**: The default VPC is a pre-configured networking environment provided by Google Cloud when you create a new project. It's designed to simplify the process of deploying resources by eliminating the need for manual network setup.
- **Subnets**: The default VPC includes one subnet in each region where resources can be deployed. These subnets are automatically created with predefined IP address ranges.
- **Firewall Policies**: Default firewall rules are automatically applied to the default VPC to allow certain types of traffic, such as SSH and RDP for remote access, while denying all other traffic by default.

### 5. Deploying Resources:

- With the default VPC set up, you can now deploy various resources such as virtual machines, databases, and other services within your project.
- When creating new resources, you'll have the option to select the default VPC, and they will automatically be provisioned within this network environment.

### Conclusion:
Congratulations! You've successfully set up a default VPC in Google Cloud Platform. You can now leverage this pre-configured networking environment to deploy and manage your resources with ease.





# Auto-Mode VPC:
- Go to the VPC network page in the GCP Console.
- Click "Create VPC network".
- ![image](https://github.com/mindmotivate/GCP/assets/130941970/d2689c32-46d9-47d9-943f-b8923ceddb11)

- Choose "Auto mode" for the VPC network mode.
![image](https://github.com/mindmotivate/GCP/assets/130941970/2dad3989-c239-4cfa-aa1d-85f3479c5506)

- Specify a name for the VPC network and click "Create".
- ![image](https://github.com/mindmotivate/GCP/assets/130941970/d0a4ae03-c1dd-4650-9ae2-cae72816fdc8)

- To create a subnet, go to the VPC network details page and click "Add subnet".
- Enter subnet details such as name, region, and IP range, and click "Create".

![image](https://github.com/mindmotivate/GCP/assets/130941970/343ce2ef-6b11-4d66-850f-0f1b191ff175)


2. **Create Firewall Rule**:
   - Click on "Create Firewall Rule" at the top of the Firewall Rules page.
### Auto Mode VPC Firewall Rules

When setting up an Auto Mode VPC in Google Cloud Platform (GCP), you'll encounter several predefined firewall rules designed to manage inbound and outbound traffic. Here's a breakdown of these rules:

### Inbound Traffic Rules:

### 1. Allow ICMP:
- Description: Permits ICMP (Internet Control Message Protocol) traffic, commonly used for network troubleshooting and diagnostics.

### 2. Allow TCP: 3389:
- Description: Permits TCP (Transmission Control Protocol) traffic on port 3389, typically used for Remote Desktop Protocol (RDP) connections to Windows instances.

### 3. Allow TCP: 22:
- Description: Permits TCP traffic on port 22, commonly used for Secure Shell (SSH) connections for remote access to instances.

## Egress Traffic Rules:

- By default, outbound traffic is allowed to egress from the VPC to external destinations without any restrictions.

## Ingress Default Rules:

- Inbound traffic from all sources (0.0.0.0/0) is denied by default.

This setup simplifies the process of managing network security within your Auto Mode VPC, providing flexibility to accommodate different use cases while ensuring a baseline level of protection.












### Custom Mode VPC:
- Go to the VPC network page in the GCP Console.
- Click "Create VPC network".
- Choose "Custom mode" for the VPC network mode.
- Specify a name for the VPC network and click "Create".
- To create subnets, go to the VPC network details page and click "Add subnet".
- Enter subnet details such as name, region, and IP range, and click "Create".

For firewall policies, you can navigate to the Firewall section within the VPC network page in the GCP Console to create and manage firewall rules for each VPC.






### Auto Mode VPC & Custom Mode VPC:
1. **Access Firewall Rules**:
   - Follow steps 1-2 above.
2. **Create Firewall Rules**:
   - Repeat steps 3-6 above to create firewall rules for SSH, RDP, HTTP/HTTPS, and ICMP.
  

### Custom Mode VPC:
1. **Access Firewall Rules**: 
   - Navigate to the VPC Network page in the GCP Console.
   - Click on "Firewall" in the left-hand menu.
2. **Create Firewall Rule**:
   - Click on "Create Firewall Rule" at the top of the Firewall Rules page.
3. **Define Rule for SSH**:
   - Name: Enter a name for the rule (e.g., allow-ssh).
   - Direction of traffic: Choose "Ingress" for inbound traffic.
   - Targets: Set the target to "All instances in the network".
   - Source filter: Choose "IP ranges".
   - Source IP ranges: Enter `0.0.0.0/0` to allow SSH from any source.
   - Protocols and ports: Specify `tcp:22` for SSH.
4. **Define Rule for RDP**:
   - Repeat the same process as for SSH, but specify `tcp:3389` for RDP.
5. **Define Rule for HTTP/HTTPS**:
   - Repeat the same process, but specify `tcp:80` and `tcp:443` for HTTP and HTTPS, respectively.
6. **Define Rule for ICMP**:
   - Repeat the same process, but specify `icmp` for ICMP traffic.






# Default VPC Configuration
resource "google_compute_network" "default_vpc" {
  name = "default-vpc"
}

# Subnet Configuration
resource "google_compute_subnetwork" "default_subnet" {
  name          = "default-subnet"
  network       = google_compute_network.default_vpc.self_link
  region        = "us-central1" # Example region
  ip_cidr_range = "10.128.0.0/20"
}

# Firewall Rules Configuration
resource "google_compute_firewall" "default_firewall_rules" {
  name          = "default-firewall-rules"
  network       = google_compute_network.default_vpc.self_link
  allow {
    protocol = "tcp"
    ports    = ["22", "3389", "80", "443"]
  }
  source_ranges = ["0.0.0.0/0"]
}

# Auto Mode VPC Configuration
resource "google_compute_network" "auto_mode_vpc" {
  name = "auto-mode-vpc"
  auto_create_subnetworks = true
}

# Custom Mode VPC Configuration
resource "google_compute_network" "custom_mode_vpc" {
  name = "custom-mode-vpc"
}

# Custom Mode Subnet Configuration
resource "google_compute_subnetwork" "custom_subnet" {
  name          = "custom-subnet"
  network       = google_compute_network.custom_mode_vpc.self_link
  region        = "us-central1" # Example region
  ip_cidr_range = "192.168.0.0/20" # Example IP range
}

# Firewall Rules for Custom Mode VPC
resource "google_compute_firewall" "custom_firewall_rules" {
  name          = "custom-firewall-rules"
  network       = google_compute_network.custom_mode_vpc.self_link
  allow {
    protocol = "tcp"
    ports    = ["22", "3389", "80", "443"]
  }
  source_ranges = ["0.0.0.0/0"]
}


# Define the GCP provider and authentication
provider "google" {
  credentials = file("<PATH_TO_SERVICE_ACCOUNT_KEY_FILE>") # Path to your service account key file
  project     = "<YOUR_PROJECT_ID>" # Your GCP project ID
  region      = "<YOUR_DEFAULT_REGION>" # Your default region
}

# Default VPC Configuration
resource "google_compute_network" "default_vpc" {
  name = "default-vpc"
}

# Subnet Configuration for Default VPC
resource "google_compute_subnetwork" "default_subnet" {
  name          = "default-subnet"
  network       = google_compute_network.default_vpc.self_link
  region        = "<YOUR_DEFAULT_REGION>" # Example region
  ip_cidr_range = "10.128.0.0/20"
}

# Firewall Rules Configuration for Default VPC
resource "google_compute_firewall" "default_firewall_rules" {
  name          = "default-firewall-rules"
  network       = google_compute_network.default_vpc.self_link
  allow {
    protocol = "tcp"
    ports    = ["22", "3389", "80", "443"]
  }
  source_ranges = ["0.0.0.0/0"]
}

# Auto Mode VPC Configuration
resource "google_compute_network" "auto_mode_vpc" {
  name = "auto-mode-vpc"
  auto_create_subnetworks = true
}

# Custom Mode VPC Configuration
resource "google_compute_network" "custom_mode_vpc" {
  name = "custom-mode-vpc"
}

# Custom Mode Subnet Configuration
resource "google_compute_subnetwork" "custom_subnet" {
  name          = "custom-subnet"
  network       = google_compute_network.custom_mode_vpc.self_link
  region        = "<YOUR_DEFAULT_REGION>" # Example region
  ip_cidr_range = "192.168.0.0/20" # Example IP range
}

# Firewall Rules for Custom Mode VPC
resource "google_compute_firewall" "custom_firewall_rules" {
  name          = "custom-firewall-rules"
  network       = google_compute_network.custom_mode_vpc.self_link
  allow {
    protocol = "tcp"
    ports    = ["22", "3389", "80", "443"]
  }
  source_ranges = ["0.0.0.0/0"]
}

