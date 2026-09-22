# CC Experiment 01 - Hypervisor Performance Analysis

## Performance Analysis of Type-1 and Type-2 Hypervisors

This experiment compares the CPU performance of a Type-1 hypervisor,
Proxmox VE, and a Type-2 hypervisor, VMware Workstation, using Ubuntu
virtual machines and the Sysbench CPU benchmark.

---

## 1. Objective

The objective of this experiment is to:

- Configure a virtual machine on Proxmox VE.
- Configure a virtual machine on VMware Workstation.
- Use comparable VM resources on both hypervisors.
- Run the same Sysbench CPU benchmark.
- Record CPU performance results.
- Compare the performance of Type-1 and Type-2 virtualization.

---

## 2. Hypervisors Used

### Type-1 Hypervisor

**Proxmox VE**

Proxmox VE was used as the Type-1 virtualization platform.
The virtual machine was configured with KVM virtualization.

### Type-2 Hypervisor

**VMware Workstation**

VMware Workstation was used as the Type-2 virtualization platform.
The Ubuntu virtual machine was executed through VMware.

---

## 3. Virtual Machine Configuration

Both virtual machines were configured with comparable resources.

| Resource | Type-1: Proxmox | Type-2: VMware |
|---|---|---|
| Guest OS | Ubuntu | Ubuntu |
| CPU | 2 vCPU | 2 vCPU |
| Memory | 2 GB | 2 GB |
| Disk | 20 GB | 20 GB |
| Benchmark | Sysbench CPU | Sysbench CPU |

### Network Configuration

- Proxmox: VirtIO with `vmbr0` bridge
- VMware: NAT

---

## 4. Benchmark Configuration

The following Sysbench CPU command was used:

```bash
sysbench cpu --cpu-max-prime=20000 run