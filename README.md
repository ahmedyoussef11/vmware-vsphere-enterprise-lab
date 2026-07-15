# Enterprise VMware vSphere Administration

## Overview

In this lab, I practiced the most common day-to-day tasks performed by VMware administrators using VMware vCenter Server.

The goal wasn't just to learn the theory, but to work directly with a vSphere environment and perform real administration tasks such as organizing workloads, creating templates, cloning virtual machines, managing snapshots, configuring DRS rules, monitoring performance, and performing live VM migration using vMotion.

---

# Lab Environment

- VMware vCenter Server
- VMware ESXi
- VMware VAMI (vCenter Server Appliance Management Interface)
- 3 ESXi Hosts
- 1 Datacenter
- 1 Compute Cluster
- Windows & Linux Virtual Machines

---

# 1. Checking the vCenter Dashboard

I started by reviewing the vCenter dashboard to check the overall status of the environment before making any changes.

From this page I could quickly verify:

- CPU usage
- Memory usage
- Storage capacity
- Connected ESXi hosts
- Running virtual machines

This is usually the first place I check before working on any VMware environment.

<img width="963" alt="Home Dashboard" src="https://github.com/user-attachments/assets/b2b9432f-5d15-4f6a-861e-1d6f0b294edc">

---

# 2. Exploring the Datacenter

Next, I explored the datacenter structure to understand how the environment was organized.

The lab contains:

- One Datacenter
- One Compute Cluster
- Two ESXi Hosts
- Multiple Virtual Machines
- Resource Pools

Understanding the inventory hierarchy is important before performing any administrative tasks.

<img width="963" alt="Datacenter Overview" src="https://github.com/user-attachments/assets/0c5c8752-e94b-4bf5-a636-344130014e5a">

---

# 3. Organizing Workloads with Resource Pools

To better organize the environment, I created three Resource Pools.

- Development
- Production
- Testing

After creating them, I moved the virtual machines into their appropriate Resource Pools.

Although this lab focused on organization, Resource Pools are also used in production environments to control CPU and memory allocation between different workloads.

---

# 4. Creating a VM Template and Cloning a Virtual Machine

Instead of installing an operating system every time, I converted **TinyLinux2** into a VM Template.

Using templates makes VM deployment much faster and keeps new virtual machines consistent.

I also cloned an existing Windows virtual machine to create another VM for testing purposes.

This is a very common task in enterprise environments when developers or testers need a copy of an existing machine.

<img width="963" alt="Clone Result" src="https://github.com/user-attachments/assets/8ca7b6af-f791-4666-aead-3d73bf29d7a8">

---

# 5. Creating a Snapshot Before Changes

Before making changes to the Windows virtual machine, I created a snapshot called:

**Before-Windows-Update**

This gives me a restore point in case something goes wrong after applying updates or changing the system configuration.

After creating the snapshot, I also tested reverting back to it successfully.

<img width="966" alt="Snapshot Management" src="https://github.com/user-attachments/assets/5ceca955-5882-4921-87f1-a62f9d01a43c">

---

# 6. Monitoring Virtual Machine Performance

I used the Performance tab inside vCenter to monitor resource usage for a virtual machine.

The metrics I checked included:

- CPU usage
- Memory usage
- Real-time performance

Monitoring these metrics helps identify resource bottlenecks and understand how virtual machines are utilizing host resources.

<img width="965" alt="Performance Monitoring" src="https://github.com/user-attachments/assets/7e873b94-0537-49c6-be48-235ab0e865ee">

---

# 7. Configuring DRS VM Rules

To practice Distributed Resource Scheduler (DRS), I created a VM Anti-Affinity Rule.

The rule was configured for:

- Windows10
- Windows10-QA

This configuration helps ensure that both virtual machines are placed on different ESXi hosts whenever possible, improving availability if one host becomes unavailable.

<img width="965" alt="DRS Rule" src="https://github.com/user-attachments/assets/887d874d-ce56-493a-8421-334b3394c1b7">

---

# 8. Performing Compute vMotion

One of the most interesting tasks in this lab was migrating a running virtual machine between ESXi hosts using **Compute vMotion**.

The migration completed without shutting down the virtual machine, demonstrating VMware's live migration capability.

Compute vMotion is commonly used during:

- Host maintenance
- Hardware upgrades
- Cluster load balancing
- Resource optimization

<img width="961" height="176" alt="Lab Console - VMware Lab Platform and 3 more pages - Personal - Microsoft​ Edge 7_15_2026 5_58_01 PM" src="https://github.com/user-attachments/assets/b84a11bf-ea9e-4f1f-9825-c77bde1228c2" />

---

# 9. Managing Cluster Configuration with Desired State

To keep all ESXi hosts configured consistently, I used **Desired State Configuration** at the cluster level.

I created a desired configuration, verified host compliance, intentionally introduced configuration drift, and finally remediated the hosts to bring them back into compliance.

This approach helps maintain configuration consistency across all ESXi hosts without configuring each host individually.

<img width="961" height="572" alt="Lab Console - VMware Lab Platform and 4 more pages - Personal - Microsoft​ Edge 7_15_2026 8_16_15 PM" src="https://github.com/user-attachments/assets/dc5bef83-23cc-49f6-a0fc-372dc79637e7" />

---

# 10. Managing vSphere Cluster Services (vCLS)

I explored how **vSphere Cluster Services (vCLS)** support cluster functionality by maintaining the services required for features such as DRS.

I also configured a Compute Policy to keep vCLS virtual machines separated from selected production workloads using Anti-Affinity rules.

<img width="965" height="570" alt="Lab Console - VMware Lab Platform and 4 more pages - Personal - Microsoft​ Edge 7_15_2026 7_51_56 PM" src="https://github.com/user-attachments/assets/f61aee0d-7fd2-448e-bcc3-de877ea1fdbb" />

---

# 11. Cross vCenter vMotion

In addition to Compute vMotion, I explored **Cross vCenter vMotion**, which allows virtual machines to be migrated between different vCenter Server instances.

This feature is useful during datacenter migrations, infrastructure consolidation, and moving workloads between independent VMware environments without rebuilding the virtual machines.

<img width="965" height="572" alt="Lab Console - VMware Lab Platform and 4 more pages - Personal - Microsoft​ Edge 7_15_2026 8_26_53 PM" src="https://github.com/user-attachments/assets/6c4548b6-f48e-476c-a6aa-117a23b235a7" />

---

# 12. Configuring vCenter Backups

To protect the management infrastructure, I configured both manual and scheduled backups for the **vCenter Server Appliance** using the **vCenter Server Appliance Management Interface (VAMI)**.

Unlike VM snapshots, VAMI backups preserve the vCenter inventory, configuration, certificates, and historical data, making them suitable for disaster recovery scenarios.

<img width="961" height="574" alt="Lab Console - VMware Lab Platform and 4 more pages - Personal - Microsoft​ Edge 7_15_2026 8_23_20 PM" src="https://github.com/user-attachments/assets/787b06f7-421b-4dfe-b3b8-e7c87282df6d" />

