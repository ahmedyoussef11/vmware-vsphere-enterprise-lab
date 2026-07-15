# VMware vSphere Enterprise Datacenter Lab

## Overview

This project demonstrates the administration of an enterprise VMware vSphere environment using VMware vCenter Server.

The objective of this lab was to simulate real-world Infrastructure Engineer tasks including resource management, virtual machine administration, templates, cloning, snapshots, **Compute vMotion**, DRS rules, performance monitoring, and workload organization.

---

# Lab Environment

- VMware vCenter Server
- VMware ESXi
- 2 ESXi Hosts
- 1 Datacenter
- 1 Compute Cluster
- Windows & Linux Virtual Machines
- Resource Pools
- VM Templates
- Virtual Machine Cloning
- Snapshots
- Compute vMotion
- DRS VM Rules
- Performance Monitoring

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

<img width="963" alt="Home Dashboard" src="https://github.com/user-attachments/assets/b2b9432f-5d15-4f6a-861e-1d6f0b294edc">

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

<img width="963" alt="Datacenter Overview" src="https://github.com/user-attachments/assets/0c5c8752-e94b-4bf5-a636-344130014e5a">

---

# 3. Organizing Workloads with Resource Pools

To simulate a production environment, Resource Pools were created to logically separate workloads based on their function.

### Development

Application servers used for software development.

### Production

Production Linux servers running business services.

### Testing

Quality Assurance virtual machines.

Virtual machines were organized into their corresponding Resource Pools, allowing administrators to manage CPU and Memory resources independently for each environment.

---

# 4. Virtual Machine Templates and Cloning

To simplify virtual machine provisioning, a reusable **VM Template** was created from the existing **TinyLinux2** virtual machine.

Using templates is considered a best practice in enterprise environments because it allows administrators to deploy standardized virtual machines without repeating the operating system installation and configuration process.

After creating the template, a new virtual machine (**Windows10-QA**) was deployed by cloning an existing Windows virtual machine.

### Benefits

- Standardized virtual machine deployments
- Faster provisioning
- Consistent operating system configuration
- Reduced deployment time
- Simplified infrastructure management

The following screenshot shows the VM Template created for future deployments.

<img width="959" alt="VM Template" src="https://github.com/user-attachments/assets/26ecfbac-844c-4c5b-9453-041faa4cc66b">

The cloned virtual machine demonstrates how VMware vCenter enables rapid deployment while maintaining identical configuration with the source VM.

<img width="963" alt="Clone Result" src="https://github.com/user-attachments/assets/8ca7b6af-f791-4666-aead-3d73bf29d7a8">

---

# 5. Snapshot Management

Before applying operating system updates, a Snapshot was created for the Windows virtual machine.

Snapshots provide a restore point that enables administrators to quickly roll back if an update or configuration change causes issues.

Snapshot created:

- **Before-Windows-Update**

This is considered a best practice before performing maintenance on production systems.

<img width="966" alt="Snapshot Management" src="https://github.com/user-attachments/assets/5ceca955-5882-4921-87f1-a62f9d01a43c">

---

# 6. Performance Monitoring

The Performance Monitor was used to analyze resource utilization for virtual machines.

Metrics monitored include:

- CPU Usage
- Memory Usage
- Real-Time Performance

Performance monitoring helps administrators detect bottlenecks and optimize resource utilization before services are affected.

<img width="965" alt="Performance Monitoring" src="https://github.com/user-attachments/assets/7e873b94-0537-49c6-be48-235ab0e865ee">

---

# 7. DRS VM Placement Rules

A DRS Anti-Affinity Rule was configured.

Rule:

- Windows10
- Windows10-QA

These virtual machines must run on different ESXi hosts whenever possible.

This improves availability by reducing the risk of both machines becoming unavailable due to a single host failure.

<img width="965" alt="DRS Rule" src="https://github.com/user-attachments/assets/887d874d-ce56-493a-8421-334b3394c1b7">

---

# 8. Virtual Machine Migration (Compute vMotion)

To simulate workload balancing within the cluster, virtual machines were migrated between ESXi hosts using **Compute vMotion**.

Compute vMotion enables administrators to move running virtual machines between hosts without downtime or service interruption.

Common enterprise use cases include:

- Load balancing
- Planned hardware maintenance
- Hardware replacement
- Cluster optimization
- Resource utilization improvement

The migration tasks completed successfully, demonstrating seamless live migration managed by VMware vCenter.

<img width="961" alt="Compute vMotion" src="https://github.com/user-attachments/assets/9314f7ce-ed9e-47d6-a45e-a5a8749a707c">

---

# Skills Demonstrated

- VMware vCenter Administration
- VMware ESXi Administration
- Enterprise Datacenter Management
- Resource Pool Management
- VM Templates
- Virtual Machine Cloning
- Snapshot Management
- Compute vMotion
- DRS VM Rules
- Performance Monitoring
- Virtual Machine Lifecycle Management
- Enterprise Virtualization

---

# Technologies Used

- VMware vSphere
- VMware vCenter Server
- VMware ESXi
- VMFS Datastore
- VMware DRS
- Compute vMotion
- Resource Pools
- VM Templates
- VMware Snapshots

---

# Author

**Ahmed Youssef**

Infrastructure & Cloud Engineer
