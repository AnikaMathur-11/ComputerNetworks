# Packet Flow Visualization Using Simulation Mode

This experiment demonstrates how Cisco Packet Tracer's Simulation Mode can be used to observe packet transmission in a simple switched network. It focuses on ARP resolution, ICMP communication using ping, and the way a switch dynamically learns MAC addresses during communication.

## Files Included

| File | Description |
|------|-------------|
| `exp_2.pkt` | Cisco Packet Tracer simulation file for packet flow visualization. |
| `exp_2.txt` | Command output and observations recorded during simulation. |
| `exp_2.pdf` | Full report containing screenshots, packet analysis, and conclusions. |
| `readme.md` | Instructions for opening, running, and understanding the experiment. |

## Requirements

- Cisco Packet Tracer (any recent version)
- 1 switch
- 3 PCs
- Copper straight-through cables
- No external hardware or additional software is required

## Network Configuration

All devices must be configured in the same subnet.

| Device | IP Address | Subnet Mask |
|--------|------------|-------------|
| PC1 | 192.168.20.1 | 255.255.255.0 |
| PC2 | 192.168.20.2 | 255.255.255.0 |
| PC3 | 192.168.20.3 | 255.255.255.0 |

Configure the IP settings on each PC through **Desktop > IP Configuration**.

## How to Open the Simulation

1. Install and launch Cisco Packet Tracer.
2. Click **File > Open** or press **Ctrl + O**.
3. Navigate to the folder containing the experiment files.
4. Select `exp_2.pkt` and open it.

## Procedure

### Step 1 - Build the Network

1. Open Cisco Packet Tracer.
2. Add the following devices:
   - 1 switch
   - 3 PCs
3. Connect each PC to the switch using copper straight-through cables.
4. Assign the IP addresses listed in the table above.

### Step 2 - Enable Simulation Mode

1. Switch Packet Tracer from **Real-Time Mode** to **Simulation Mode**.
2. Open the event filter settings.
3. Keep only the following protocols visible:
   - ARP
   - ICMP

This makes it easier to observe only the relevant packet flow during testing.

### Step 3 - First Ping Test (PC1 to PC2)

1. Click on **PC1**.
2. Go to **Desktop > Command Prompt**.
3. Run the following command:

   ```
   ping 192.168.20.2
   ```

4. Observe the event list and packet movement carefully.

#### Expected observation

- ARP Request is sent as a broadcast.
- ARP Reply is returned as a unicast.
- ICMP Echo Request is sent from PC1 to PC2.
- ICMP Echo Reply is sent from PC2 back to PC1.

The first ping takes slightly longer because the sender must first resolve the destination MAC address.

### Step 4 - Second Ping Test (PC1 to PC2)

1. Run the same ping command again:

   ```
   ping 192.168.20.2
   ```

2. Observe the packet flow in Simulation Mode.

#### Expected observation

- No ARP Request is generated this time.
- Only ICMP Echo Request and Echo Reply packets appear.

This happens because the destination MAC address has already been learned and stored in the ARP cache.

### Step 5 - Observe MAC Address Learning

1. Click on the switch.
2. If CLI access is available, use the following command:

   ```
   show mac address-table
   ```

3. If CLI access is not used, infer the switch behavior through packet movement in Simulation Mode.

#### Expected observation

- The switch learns the source MAC address of incoming frames.
- It maps each learned MAC address to the corresponding switch port.
- Once learned, frames are forwarded more efficiently to the correct destination port.

## Packet Behavior Summary

### Event sequence during first ping

1. ARP Request
2. ARP Reply
3. ICMP Echo Request
4. ICMP Echo Reply

### Event sequence during second ping

1. ICMP Echo Request
2. ICMP Echo Reply

## First Ping vs Second Ping

| Feature | First Ping | Second Ping |
|---------|------------|-------------|
| ARP involved | Yes | No |
| ICMP packets | Yes | Yes |
| Speed | Slower | Faster |
| Reason | MAC address not yet known | MAC address already cached |

## Key Observations

- ARP Requests are broadcast to all devices in the local network.
- ARP Replies are unicast back to the sender.
- A switch dynamically learns MAC addresses by examining source addresses in incoming frames.
- After address resolution, ICMP packets are forwarded more efficiently.
- Simulation Mode helps visualize each stage of packet exchange clearly.

## Conclusion

This experiment helps in understanding how address resolution and packet forwarding work in a local area network. It also demonstrates the role of ARP in initial communication and the importance of MAC address learning in switch-based forwarding.
