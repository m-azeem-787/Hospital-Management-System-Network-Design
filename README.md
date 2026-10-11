# Hospital Management System — Network Design

A **Cisco Packet Tracer** network simulation for a hospital environment. The design separates hospital departments into VLANs to organize network traffic and support communication between reception, doctors, administration, nursing stations, and servers.

## Project Objectives

- Segment hospital departments into separate VLANs.
- Configure IP subnets and default gateways for each department.
- Use routers and switches to support communication between VLANs.
- Provide centralized DHCP addressing and an FTP service for file transfers.
- Keep the design expandable so additional devices can be added to the relevant department network.

## Network Topology

The topology contains two routers connected through a serial link. Each router connects to a switch, and the switches connect the departmental devices and servers.

<img width="974" height="511" alt="image" src="https://github.com/user-attachments/assets/126c3384-f44e-4c9f-b042-a602e177225e" />

## VLANs and IP Addressing

The report uses `/24` subnets (`255.255.255.0`) and identifies `.1` as the intended default gateway for each department network.

| VLAN | Department | Network | Intended Default Gateway | Devices |
|---:|---|---|---|---|
| 10 | Reception | `192.168.10.0/24` | `192.168.10.1` | PC0, PC1 |
| 20 | Servers | `192.168.20.0/24` | `192.168.20.1` | Main server, Backup server |
| 30 | Doctors | `192.168.30.0/24` | `192.168.30.1` | PC2, Laptop0 |
| 40 | Administration & Nurses | `192.168.40.0/24` | `192.168.40.1` | PC3, PC4, PC5 |

## Main Components

- **Routers (Router0 and Router1):** Handle routing for the department networks and connect to each other through the serial link.
- **Switches (Switch0 and Switch1):** Connect end devices and carry the required VLAN traffic over configured trunk links.
- **Main server:** Configured to provide DHCP services for IP address assignment.
- **Backup server:** Configured with an FTP service for file storage and transfer.
- **End devices:** PCs and a laptop representing reception, doctors, administration, and nursing staff.

## Services

### DHCP

The main server is used to assign IP configuration dynamically through DHCP pools for the hospital networks. The addressing shown in the report uses `8.8.8.8` as the DNS server.

### FTP

The backup server has its FTP service enabled to support file transfer. Use the server's configured account details when testing FTP from a client device; do not publish passwords in this repository.

## Scope

This repository contains a **networking lab simulation**, not a complete hospital management software application. The network is intended for learning and demonstration in Cisco Packet Tracer.
