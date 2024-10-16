---
modified: 2024-09-30T17:17:34+02:00
cssclasses:
  - wide-table
---
## IP Block and Subnet Assignments

• **Location A**: 10.1.0.0/16

• **Location B**: 10.2.0.0/16

## Network Assignments with Gateway and Broadcast Addresses


### Location A

| **Network** | **VLAN ID** | **IP Subnet (Location A)** | **Default Gateway** | **Broadcast Address** | **Description**                                     | **Native IPv6 Subnet** | **Native IPv6 Default Gateway** |
| ----------- | ----------- | -------------------------- | ------------------- | --------------------- | --------------------------------------------------- | ---------------------- | ------------------------------- |
| **srv**     | 10          | `10.1.10.0/24`             | `10.1.10.1`         | `10.1.10.255`         | Server-to-server communication (~200 devices)       | `2001:db8:1:10::/64`   | `2001:db8:1:10::1`              |
| **fe**      | 20          | `10.1.20.0/24`             | `10.1.20.1`         | `10.1.20.255`         | Frontend network for clients in `cnt`               | `2001:db8:1:20::/64`   | `2001:db8:1:20::1`              |
| **mgmt**    | 30          | `10.1.30.0/24`             | `10.1.30.1`         | `10.1.30.255`         | Management network for out-of-band physical servers | `2001:db8:1:30::/64`   | `2001:db8:1:30::1`              |
| **sto**     | 40          | `10.1.40.0/24`             | `10.1.40.1`         | `10.1.40.255`         | Storage network for storage servers                 | `2001:db8:1:40::/64`   | `2001:db8:1:40::1`              |
| **pod**     | 50          | `10.1.50.0/23`             | `10.1.50.1`         | `10.1.51.255`         | Network for Docker/Kubernetes containers            | `2001:db8:1:50::/64`   | `2001:db8:1:50::1`              |
| **cnt**     | 60          | `10.1.60.0/23`             | `10.1.60.1`         | `10.1.61.255`         | Client network                                      | `2001:db8:1:60::/64`   | `2001:db8:1:60::1`              |
| **iot**     | 70          | `10.1.70.0/23`             | `10.1.70.1`         | `10.1.71.255`         | IoT network for home automation, printers, etc.     | `2001:db8:1:70::/64`   | `2001:db8:1:70::1`              |

### Location B

| **Network** | **VLAN ID** | **IP Subnet (Location B)** | **Default Gateway** | **Broadcast Address** | **Description**                                     | **Native IPv6 Subnet**                   | **Native IPv6 Default Gateway**     |
| ----------- | ----------- | -------------------------- | ------------------- | --------------------- | --------------------------------------------------- | ---------------------------------------- | ----------------------------------- |
| **srv**     | 10          | `10.2.10.0/24`             | `10.2.10.1`         | `10.2.10.255`         | Server-to-server communication (~200 devices)       | `2001:db8:2:10::/64`                    | `2001:db8:2:10::1`                  |
| **fe**      | 20          | `10.2.20.0/24`             | `10.2.20.1`         | `10.2.20.255`         | Frontend network for clients in `cnt`               | `2001:db8:2:20::/64`                    | `2001:db8:2:20::1`                  |
| **mgmt**    | 30          | `10.2.30.0/24`             | `10.2.30.1`         | `10.2.30.255`         | Management network for out-of-band physical servers | `2001:db8:2:30::/64`                    | `2001:db8:2:30::1`                  |
| **sto**     | 40          | `10.2.40.0/24`             | `10.2.40.1`         | `10.2.40.255`         | Storage network for storage servers                 | `2001:db8:2:40::/64`                    | `2001:db8:2:40::1`                  |
| **pod**     | 50          | `10.2.50.0/23`             | `10.2.50.1`         | `10.2.51.255`         | Network for Docker/Kubernetes containers            | `2001:db8:2:50::/64`                    | `2001:db8:2:50::1`                  |
| **cnt**     | 60          | `10.2.60.0/23`             | `10.2.60.1`         | `10.2.61.255`         | Client network                                      | `2001:db8:2:60::/64`                    | `2001:db8:2:60::1`                  |
| **iot**     | 70          | `10.2.70.0/23`             | `10.2.70.1`         | `10.2.71.255`         | IoT network for home automation, printers, etc.     | `2001:db8:2:70::/64`                    | `2001:db8:2:70::1`                  |
