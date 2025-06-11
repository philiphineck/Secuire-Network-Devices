# Packet Tracer Lab: Secure Network Devices
This exercise has hands-on activity that equips any network practitioner with requisite skills to thrive in the network environment

---

## **Lab 2: Secure Network Devices (New Lab)**

### Scenario

This lab focuses on configuring a Cisco router (RTR-A) and a switch (SW-1) with a set of robust security measures in preparation for network deployment. Key aspects include secure password management, SSH enablement, and interface hardening.

### Objectives

* Prevent IOS from resolving mistyped commands.
* Configure hostnames according to the addressing table.
* Enforce minimum password length.
* Set strong console and privileged EXEC mode passwords.
* Configure session timeouts.
* Enable password encryption.
* Implement a MOTD banner.
* Create local user accounts with encrypted passwords.
* Enable and configure SSH (domain name, modulus).
* Block brute force login attempts.
* Disable all unused switch ports.
* Configure switch management interface for network access.
* Ensure hosts can ping the switch management interface.

### Addressing Table

| Device    | Interface | IP Address    | Subnet Mask     | Default Gateway |
| :-------- | :-------- | :------------ | :-------------- | :-------------- |
| RTR-A     | G0/0/0    | 192.168.1.1   | 255.255.255.0   | N/A             |
| RTR-A     | G0/0/1    | 192.168.2.1   | 255.255.255.0   | N/A             |
| SW-1      | SVI       | 192.168.1.254 | 255.255.255.0   | blank           |
| PC        | NIC       | 192.168.1.2   | 255.255.255.0   | blank           |
| Laptop    | NIC       | 192.168.1.10  | 255.255.255.0   | blank           |
| Remote PC | NIC       | 192.168.2.10  | 255.255.255.0   | blank           |

### Key Configuration Commands & Approach


* **RTR-A Configuration:**
    * `no ip domain-lookup` (to prevent mistyped command resolution)
    * `security password min-length 10`
    * `enable secret @Cons1234!` (or your chosen strong password)
    * `banner motd #Unauthorized access strictly prohibited!#`
    * `service password-encryption`
    * `username NETadmin secret LogAdmin!9`
    * `ip domain-name security.com`
    * `crypto key generate rsa modulus 1024`
    * `login block-for 45 attempts 3 within 100`
    * `line console 0` and `line vty 0 4` configuration for `exec-timeout 7 0`, `transport input ssh`, `login local`.
* **SW-1 Configuration:**
    * `interface range F0/2-24, G0/2` followed by `shutdown` (for unused ports).
    * `interface vlan 1` IP configuration and `no shutdown`.
    * `ip default-gateway 192.168.1.1`
    * `enable secret @Cons1234!`
    * `username NETadmin secret LogAdmin!9`
    * SSH configuration (similar to router).
    * `line vty 0 15` (depending on switch model) for `transport input ssh` and `login local`.


### Files in this Repository

* `PacketTracer_SecureNetworkDevices_Lab.pka`: The Packet Tracer file for this lab.
* `screenshots/secure_network_devices_lab/`: Directory containing screenshots for this lab and topology.
* `Secure_Network_Devices_Instructions.md`: Original lab instructions.

### Key Lessons Learned

* Understanding the practical application of various security hardening commands on Cisco IOS devices.
* The critical role of SSH in securing remote administrative access compared to unencrypted protocols.
* Importance of banners, minimum password length, and login blocking for foundational security.
* Best practices for switch port security by disabling unused interfaces.
* The systematic approach to implementing security configurations on different network device types.

---

**Philiphine Cheptanui | Information Scientist, BSc | Computer Network | Cybersecurity | WordPress | Data Entry | Research | Writer.**


---

## 🌐 Connect with me:

 [LinkedIn](https://linkedin.com/in/philiphinecheptanui) &emsp;&emsp;
 [Email](koimaphilipine@gmail.com) &emsp;&emsp;
 [PortFolio Blog](https://compnetworksecurity.blogspot.com/) &emsp;&emsp;
 [Repository](https://github.com/philiphineck/Use-Wireshark-to-View-Network-Traffic) 
