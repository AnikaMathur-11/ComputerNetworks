# Basic Network Topologies - Experiment 1

This folder contains the files for **Experiment 1: Basic Network Topologies** created in Cisco Packet Tracer. The simulation demonstrates the behavior of different network layouts, including star topology using a switch, star topology using a hub, and a ring-like switched topology with Spanning Tree Protocol (STP).

## Files Included

| File | Description |
|------|-------------|
| `exp_1.pkt` | Cisco Packet Tracer simulation file containing all topology-based tasks. |
| `exp_1.txt` | Ping outputs and short observations recorded for each task. |
| `exp_1.pdf` | Complete report with topology screenshots, test results, observations, and conclusions. |
| `readme.md` | Instructions for opening the simulation and verifying each topology. |

## Requirements

- Cisco Packet Tracer Student version 6.2 or later is recommended.
- Packet Tracer can be downloaded from Cisco NetAcad using a free account.
- No additional hardware or software is required.
- All tasks run completely inside the Packet Tracer environment.

## Opening the Simulation

1. Install and open Cisco Packet Tracer.
2. Go to **File > Open** or press **Ctrl + O**.
3. Browse to the folder containing the submission files.
4. Select `exp_1.pkt` and open it.

## Topology Verification

### Task 1 - Star Topology using Switch

**Devices:** 1 switch and 4 PCs  
**IP addresses:**

- PC0 -> 192.168.0.1
- PC1 -> 192.168.0.2
- PC2 -> 192.168.0.3
- PC3 -> 192.168.0.4

**Steps to test:**

1. Open **PC0 > Desktop > Command Prompt**.
2. Run the following commands:
   ```
   ping 192.168.0.2
   ping 192.168.0.3
   ping 192.168.0.4
   ```
3. Observe that the first transmission involves ARP activity, while later packets are forwarded directly to the intended destination.

### Task 2 - Star Topology using Hub

**Devices:** 1 hub and 4 PCs  
**IP addresses:**

- PC0 -> 192.168.0.1
- PC1 -> 192.168.0.2
- PC2 -> 192.168.0.3
- PC3 -> 192.168.0.4

**Steps to test:**

1. Open **PC1 > Desktop > Command Prompt**.
2. Run the following commands:
   ```
   ping 192.168.0.2
   ping 192.168.0.3
   ping 192.168.0.4
   ```
3. Switch to **Simulation Mode** and monitor frame movement.
4. Notice that the hub forwards every frame to all connected ports.

**Observation:** Since a hub does not make forwarding decisions, all connected devices receive the transmitted frames.

### Task 3 - Ring-like Topology with STP

**Devices:** 3 switches connected in a loop with 8 PCs distributed across the network  
**IP addresses:**

- PC0 -> 192.168.0.1
- PC1 -> 192.168.0.2
- PC2 -> 192.168.0.3
- PC3 -> 192.168.0.4
- PC4 -> 192.168.0.5
- PC5 -> 192.168.0.6
- PC6 -> 192.168.0.7
- PC7 -> 192.168.0.8

**Steps to test:**

1. Open **PC0 > Desktop > Command Prompt**.
2. Run the following commands:
   ```
   ping 192.168.0.5
   ping 192.168.0.8
   ```
3. Observe that STP blocks one redundant link to avoid switching loops.
4. Verify that traffic moves through the active path selected by the protocol.

### Task 3 Extension - Link Failure Test

**Setup:** Same topology as Task 3

**Steps to test:**

1. First verify connectivity between PCs placed on different switches.
2. Remove one active inter-switch connection to simulate a link failure.
3. Wait a few seconds for STP to recompute the topology.
4. Repeat the ping test and verify that communication resumes through the alternate path.

## Notes

This experiment is intended to demonstrate how network devices handle traffic in different topologies and how STP helps maintain network stability when redundant paths exist.
