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
The Ubuntu virtual machine was executed through VMware Workstation.

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

# 4. Type-1 Hypervisor - Proxmox VE

## 4.1 VM Configuration

The Proxmox virtual machine was configured with:

- CPU: 2 vCPU
- Memory: 2048 MB
- Disk: 20 GB
- CPU type: x86-64-v2-AES
- Network: VirtIO
- Bridge: vmbr0
- Guest OS: Ubuntu 22.04.5 LTS
- Virtualization: KVM

---

## 4.2 Type-1 VM Commands

### Check system information

```bash
hostnamectl
Check CPU configuration
lscpu
Check memory configuration
free -h
Check disk configuration
df -h
Monitor system resources
top

Press q to exit top.

4.3 Install Sysbench

Update the Ubuntu package repository:

sudo apt update

Install Sysbench:

sudo apt install sysbench -y

Check the installed Sysbench version:

sysbench --version
4.4 Type-1 CPU Benchmark

The CPU benchmark was executed using:

sysbench cpu --cpu-max-prime=20000 run

The benchmark uses a prime-number limit of 20000.

Record the following values from the output:

Total execution time
Total number of events
Events per second
Minimum latency
Average latency
Maximum latency
4.5 Type-1 Observation
Parameter	Observation
Hypervisor	Proxmox VE
Hypervisor Type	Type-1
Guest Operating System	Ubuntu
CPU Allocation	2 vCPU
Memory Allocation	2 GB
Disk Allocation	20 GB
Network	VirtIO / vmbr0
Total Execution Time	Record from Sysbench output
Total Events	Record from Sysbench output
Events per Second	Record from Sysbench output
Minimum Latency	Record from Sysbench output
Average Latency	Record from Sysbench output
Maximum Latency	Record from Sysbench output
5. Type-2 Hypervisor - VMware Workstation
5.1 VM Configuration

The VMware Workstation virtual machine was configured with:

CPU: 2 vCPU
Memory: 2048 MB
Disk: 20 GB
Guest OS: Ubuntu
Network: NAT
Hypervisor Type: Type-2
5.2 Type-2 VM Commands
Check system information
hostnamectl
Check CPU configuration
lscpu
Check memory configuration
free -h
Check disk configuration
df -h
Monitor system resources
top

Press q to exit top.

5.3 Install Sysbench

Update the Ubuntu package repository:

sudo apt update

Install Sysbench:

sudo apt install sysbench -y

Verify the installation:

sysbench --version
5.4 Type-2 CPU Benchmark

The CPU benchmark was executed using:

sysbench cpu --cpu-max-prime=20000 run

The benchmark uses a prime-number limit of 20000.

Note

The command was initially entered incorrectly using:

sysbench cpu --cpu-max-price=20000 run

This produced an invalid option error.

The correct option is:

--cpu-max-prime=20000

Therefore, the correct benchmark command is:

sysbench cpu --cpu-max-prime=20000 run
5.5 Type-2 Benchmark Result

The VMware Workstation benchmark produced the following results:

sysbench 1.0.20

Number of threads: 1

Prime numbers limit: 20000

CPU speed:
    events per second: 1058.76

General statistics:
    total time:              10.0002s
    total number of events:  10589

Latency (ms):
    min:                     0.72
    avg:                     0.94
    max:                     5.32
    95th percentile:         1.61
    sum:                     9985.42

Threads fairness:
    events (avg/stddev):     10589.0000/0.00
    execution time (avg/stddev): 9.9854/0.00
5.6 Type-2 Observation Table
Parameter	Observation
Hypervisor	VMware Workstation
Hypervisor Type	Type-2
Guest Operating System	Ubuntu
CPU Allocation	2 vCPU
Memory Allocation	2 GB
Disk Allocation	20 GB
Network	NAT
Sysbench Version	1.0.20
CPU Prime Limit	20000
Total Execution Time	10.0002 s
Total Events	10589
Events per Second	1058.76
Minimum Latency	0.72 ms
Average Latency	0.94 ms
Maximum Latency	5.32 ms
95th Percentile Latency	1.61 ms
6. Commands Used in the Experiment
Type-1 - Proxmox VE
hostnamectl
lscpu
free -h
df -h
top
sudo apt update
sudo apt install sysbench -y
sysbench --version
sysbench cpu --cpu-max-prime=20000 run
Type-2 - VMware Workstation
hostnamectl
lscpu
free -h
df -h
top
sudo apt update
sudo apt install sysbench -y
sysbench --version
sysbench cpu --cpu-max-prime=20000 run
7. Performance Results
Type-1 Hypervisor
Performance Metric	Result
Hypervisor	Proxmox VE
Hypervisor Type	Type-1
CPU	2 vCPU
Memory	2 GB
Disk	20 GB
Total Execution Time	Record from Type-1 Sysbench output
Total Events	Record from Type-1 Sysbench output
Events per Second	Record from Type-1 Sysbench output
Minimum Latency	Record from Type-1 Sysbench output
Average Latency	Record from Type-1 Sysbench output
Maximum Latency	Record from Type-1 Sysbench output
Type-2 Hypervisor
Performance Metric	Result
Hypervisor	VMware Workstation
Hypervisor Type	Type-2
CPU	2 vCPU
Memory	2 GB
Disk	20 GB
Total Execution Time	10.0002 s
Total Events	10589
Events per Second	1058.76
Minimum Latency	0.72 ms
Average Latency	0.94 ms
Maximum Latency	5.32 ms
8. Comparison

Both virtual machines were configured with comparable resources:

Parameter	Type-1: Proxmox	Type-2: VMware
Hypervisor	Proxmox VE	VMware Workstation
Hypervisor Type	Type-1	Type-2
Guest OS	Ubuntu	Ubuntu
CPU	2 vCPU	2 vCPU
Memory	2 GB	2 GB
Disk	20 GB	20 GB
Network	VirtIO / vmbr0	NAT
Benchmark	Sysbench CPU	Sysbench CPU
Prime Limit	20000	20000

The same Sysbench CPU benchmark was used on both virtual machines so that
the recorded CPU performance results can be compared using the measured
execution time, events per second, and latency values.

9. Conclusion

The experiment demonstrates CPU performance testing of virtual machines
running on a Type-1 hypervisor (Proxmox VE) and a Type-2 hypervisor
(VMware Workstation).

Both virtual machines were configured with 2 vCPU, 2 GB RAM, and a 20 GB
virtual disk. The same Sysbench CPU benchmark with a prime limit of 20000
was used for the performance measurement.

The Type-2 VMware benchmark recorded:

Total execution time: 10.0002 seconds
Total events: 10589
Events per second: 1058.76
Average latency: 0.94 ms

The Type-1 benchmark values should be entered from the corresponding
Sysbench output recorded during the Proxmox experiment.

10. VM Shutdown

After completing the experiment, the virtual machine can be shut down
using:

sudo poweroff

For VMware Workstation, the guest can alternatively be shut down using:

VM -> Power -> Shut Down Guest
