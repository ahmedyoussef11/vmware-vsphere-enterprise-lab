# VMware vSphere Enterprise Administration Hands-on Lab

## Overview

In this lab, I practiced the most common day-to-day tasks performed by VMware administrators using VMware vCenter Server.

The goal wasn't just to learn the theory, but to work directly with a vSphere environment and perform real administration tasks such as organizing workloads, creating templates, cloning virtual machines, managing snapshots, configuring DRS rules, monitoring performance, and performing live VM migration using vMotion.

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
- Snapshot Management
- Compute vMotion (Live Migration)
- DRS VM Rules (Affinity / Anti-Affinity)
- Performance Monitoring

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

<img width="961" alt="Compute vMotion" src="https://github.com/user-attachments/assets/9314f7ce-ed9e-47d6-a45e-a5a8749a707c">

---

# What I Learned

Through this lab, I gained hands-on experience with several common VMware administration tasks.

Instead of only reading about these features, I configured and tested them directly inside VMware vCenter, which gave me a much better understanding of how they are used in real enterprise environments.
