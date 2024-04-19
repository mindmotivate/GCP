***Create an Auto Mode VPC named "auto-vpc-tf"***

```hcl
resource "google_compute_network" "auto-vpc-tf" {
  name = "auto-vpc-tf"
  auto_create_subnetworks = true
}
```

- This code block creates an Auto Mode VPC named "auto-vpc-tf".
- `auto_create_subnetworks = true` indicates that subnetworks will be automatically created within this VPC.


***Create a Custom Mode VPC named "custom-vpc-tf"***

```hcl
resource "google_compute_network" "custom-vpc-tf" {
  name = "custom-vpc-tf"
  auto_create_subnetworks = false
}
```


- This code block creates a Custom Mode VPC named "custom-vpc-tf".
- `auto_create_subnetworks = false` indicates that subnetworks will not be automatically created within this VPC.


***Create a Subnet named "sub-sg" within the Custom Mode VPC***

```hcl
resource "google_compute_subnetwork" "sub-sg" {
  name = "sub-sg"
  network = google_compute_network.custom-vpc-tf.id
  ip_cidr_range = "10.1.0.0/24"
  region = "asia-southeast1"
  private_ip_google_access = true
}
```
- This code block creates a subnet named "sub-sg" within the Custom Mode VPC "custom-vpc-tf".
- `ip_cidr_range` specifies the IP address range for the subnet.
- `region` specifies the region where the subnet will be located.
- `private_ip_google_access = true` enables Google private access for the subnet.

***Create a firewall rule named "allow-icmp" to allow ICMP traffic***

```hcl
resource "google_compute_firewall" "allow-icmp" {
  name = "allow-icmp"
  network = google_compute_network.custom-vpc-tf.id
  allow {
    protocol = "icmp"
  }
  source_ranges = ["49.36.82.10/32"]
  priority = 455
}
```

- This code block creates a firewall rule named "allow-icmp" within the Custom Mode VPC "custom-vpc-tf".
- The rule allows ICMP traffic.
- `source_ranges` specifies the allowed source IP range.
- `priority` determines the order in which the firewall rule is evaluated relative to other rules.

***Output the ID of the Auto Mode VPC***

```hcl
output "auto" {
  value = google_compute_network.auto-vpc-tf.id
}
```

***Output the ID of the Custom Mode VPC***

```hcl
output "custom" {
  value = google_compute_network.custom-vpc-tf.id
}
```

