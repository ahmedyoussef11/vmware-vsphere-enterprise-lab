# VMware vSphere Enterprise Datacenter Lab

## Overview

This project demonstrates the administration of an enterprise VMware vSphere environment using VMware vCenter Server.

The objective of this lab was to simulate real-world Infrastructure Engineer tasks including resource management, virtual machine administration, templates, snapshots, DRS rules, monitoring, and workload organization.

---

# Lab Environment

- VMware vCenter Server
- 2 ESXi Hosts
- 1 Datacenter
- 1 Cluster
- Windows & Linux Virtual Machines
- Resource Pools
- VM Templates
- Snapshots
- DRS Rules

---

# 1. vCenter Home Dashboard

The first step was verifying the overall health of the virtual infrastructure.

The dashboard provides a quick overview of:

- CPU utilization
- Memory utilization
- Storage capacity
- Connected Hosts
- Running Virtual Machines

This is usually the first screen an administrator checks before performing any operation.

![Home Dashboard](<img width="963" height="540" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_53_31 PM" src="https://github.com/user-attachments/assets/b2b9432f-5d15-4f6a-861e-1d6f0b294edc" />
)

---

# 2. Datacenter Structure

The virtual infrastructure contains one Datacenter with one Compute Cluster managed by VMware vCenter.

Inside the cluster are:

- Two ESXi Hosts
- Development Resource Pool
- Production Resource Pool
- Testing Resource Pool
- Multiple Virtual Machines

This hierarchy represents how enterprise environments are organized.

![Datacenter Overview](<img width="963" height="539" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_53_56 PM" src="https://github.com/user-attachments/assets/0c5c8752-e94b-4bf5-a636-344130014e5a" />
)

---

# 3. Organizing Workloads with Resource Pools

To simulate a production environment, Resource Pools were created for different workloads.

## Development

Application servers used for software development.

## Production

Production Linux servers running business services.

## Testing

Quality Assurance virtual machines.

After creating the pools, virtual machines were migrated into their corresponding Resource Pools.

Example:

Development
- app-serv01
- web-serv01

Production
- TinyLinux
- TinyLinux2

Testing
- Windows10

This allows administrators to manage CPU and Memory resources independently for each department.


---

# 4. Virtual Machine Templates and Cloning

To simplify virtual machine provisioning, a reusable **VM Template** was created from the existing **TinyLinux2** virtual machine.

Using templates is considered a best practice in enterprise environments because it allows administrators to deploy standardized virtual machines without repeating the operating system installation and configuration process.

After creating the template, a new virtual machine (**Windows10-QA**) was deployed by cloning an existing Windows virtual machine. This demonstrates how vCenter accelerates VM provisioning while ensuring consistency across deployments.

### Benefits

- Standardized virtual machine deployments
- Faster provisioning
- Consistent operating system configuration
- Reduced deployment time
- Simplified infrastructure management

The following screenshot shows the VM Template that was created and used for future deployments.

<img width="959" height="543" alt="VM Template" src="https://github.com/user-attachments/assets/26ecfbac-844c-4c5b-9453-041faa4cc66b" />

After that, a new virtual machine (**Windows10-QA**) was successfully created by cloning the existing **Windows10** machine, demonstrating rapid deployment capabilities available in VMware vCenter.

![Clone Result](<img width="963" height="542" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_55_34 PM" src="https://github.com/user-attachments/assets/8ca7b6af-f791-4666-aead-3d73bf29d7a8" />
)

---

# 5. Snapshot Management

Before making changes to a production virtual machine, a Snapshot was created.

Snapshots provide a restore point that allows administrators to quickly roll back if a software update or configuration change fails.

The snapshot created:

- Before-Windows-Update

This is considered a best practice before major maintenance.

![Snapshot](<img width="966" height="543" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_56_53 PM" src="https://github.com/user-attachments/assets/5ceca955-5882-4921-87f1-a62f9d01a43c" />
)

---

# 6. Performance Monitoring

The Performance Monitor was used to observe the resource utilization of the Web Server.

Metrics monitored include:

- CPU Usage
- Memory Usage
- Real-time Performance

Monitoring allows administrators to detect bottlenecks before they impact users.

![Performance Monitoring](<img width="965" height="541" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 6_00_48 PM" src="https://github.com/user-attachments/assets/7e873b94-0537-49c6-be48-235ab0e865ee" />
)

---

# 7. DRS VM Placement Rules

A DRS Anti-Affinity Rule was configured.

Rule:

Windows10

must not run on

Windows10-QA

Purpose:

If one ESXi Host fails, both virtual machines will not be affected simultaneously.

This increases availability inside the cluster.

![DRS Rule](<img width="965" height="542" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_59_02 PM" src="https://github.com/user-attachments/assets/887d874d-ce56-493a-8421-334b3394c1b7" />
)

---

# 8. Virtual Machine Migration (Compute vMotion)

To simulate workload balancing within the cluster, several virtual machines were migrated between ESXi hosts using **Compute vMotion**.

Compute vMotion enables administrators to move a running virtual machine from one ESXi host to another without downtime or service interruption. This feature is commonly used for:

- Load balancing across hosts
- Planned maintenance
- Hardware upgrades
- Improving cluster resource utilization

The migration tasks completed successfully, demonstrating seamless live migration managed by VMware vCenter.


![Recent Tasks](<img width="961" height="545" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_58_01 PM" src="https://github.com/user-attachments/assets/9314f7ce-ed9e-47d6-a45e-a5a8749a707c" />
)
