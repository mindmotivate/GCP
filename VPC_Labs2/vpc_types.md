# Default VPC:
- **Description**: When you create a new project in GCP, a default VPC is automatically provisioned for you. It's a ready-to-use VPC with default settings that allow you to quickly deploy resources without additional configuration.
- **Subnets**: By default, a default VPC includes one subnet in each region where resources can be deployed. These subnets are created with predefined IP ranges.
- **Firewall Policies**: Default firewall rules are automatically applied to the default VPC to allow certain types of traffic, such as SSH and RDP for remote access, and deny all other traffic by default.

# Auto Mode VPC:
- **Description**: Auto Mode VPC allows you to create subnets with predefined IP ranges automatically. When you create a subnet in Auto Mode, GCP automatically assigns IP addresses from a predefined range for that region.
- **Subnets**: Subnets in Auto Mode VPCs are created with predefined IP ranges based on the region. Each subnet is automatically created within the VPC when you deploy resources.
- **Firewall Policies**: Similar to Default VPC, Auto Mode VPC comes with default firewall rules applied to control incoming and outgoing traffic. These rules can be customized as needed.

# Custom Mode VPC:
- **Description**: Custom Mode VPC provides full control over the VPC configuration, allowing you to define custom IP ranges and subnets.
- **Subnets**: In Custom Mode VPC, you can define your own IP ranges and create subnets within those ranges. You have flexibility in defining the size and range of each subnet.
- **Firewall Policies**: Custom Mode VPC allows you to define custom firewall rules to control inbound and outbound traffic. You can create rules based on specific IP ranges, protocols, and ports, providing granular control over network traffic.

## Tutorial for Setting Up Each Type of VPC:
### Default VPC:
- Simply create a new project in GCP, and the default VPC will be automatically provisioned for you. You can start deploying resources immediately without any additional setup.

### Auto Mode VPC:
- Go to the VPC network page in the GCP Console.
- Click "Create VPC network".
- Choose "Auto mode" for the VPC network mode.
- Specify a name for the VPC network and click "Create".
- To create a subnet, go to the VPC network details page and click "Add subnet".
- Enter subnet details such as name, region, and IP range, and click "Create".

### Custom Mode VPC:
- Go to the VPC network page in the GCP Console.
- Click "Create VPC network".
- Choose "Custom mode" for the VPC network mode.
- Specify a name for the VPC network and click "Create".
- To create subnets, go to the VPC network details page and click "Add subnet".
- Enter subnet details such as name, region, and IP range, and click "Create".

For firewall policies, you can navigate to the Firewall section within the VPC network page in the GCP Console to create and manage firewall rules for each VPC.





### Default VPC:
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

### Auto Mode VPC & Custom Mode VPC:
1. **Access Firewall Rules**:
   - Follow steps 1-2 above.
2. **Create Firewall Rules**:
   - Repeat steps 3-6 above to create firewall rules for SSH, RDP, HTTP/HTTPS, and ICMP.
  
  ### Auto Mode VPC:
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

