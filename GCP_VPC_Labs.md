# Lab 1 – Default VPC

## Setup
1. Create a new project or select an existing project.
2. Optionally, create an organization and location.

## Creating Default VPC
1. Navigate to **VPC networks**.
2. Click **Create**.
3. Enable Compute Engine when prompted.
4. Explore the default VPC and its subnets under the **Networks** tab.

### Notes:
- If VPC creation is not complete, navigate to the **Network Interfaces** tab.
- Select **Network** to see the default option.
- Remember, in production environments, avoid using the default VPC.

## Firewall Rules
1. Check the **Firewall Rules** tab.
2. Four auto-created rules should be present:
    - ICMP allow
    - Allow internal
    - Allow RDP
    - Allow SSH

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




