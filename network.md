<h2 align=center>Networking Concepts</h2>

**Introduction to Networking**

Networking is the practice of connecting computers and other devices to share resources and information. It involves hardware, software, and protocols that enable communication between devices.

**Types of Networks (LAN, WAN, etc.)**

- **LAN (Local Area Network):** A network that connects devices within a limited area, such as a home, school, or office building.
- **WAN (Wide Area Network):** A network that covers a broad area, such as a city, country, or even global connections.
- **MAN (Metropolitan Area Network):** A network that spans a city or a large campus.
- **PAN (Personal Area Network):** A network for personal devices, typically within a range of a few meters.

**Network Topologies**

- **Bus Topology:** All devices are connected to a single central cable.
- **Star Topology:** All devices are connected to a central hub.
- **Ring Topology:** Each device is connected to two other devices, forming a ring.
- **Mesh Topology:** Devices are interconnected, with multiple paths between them.

**OSI and TCP/IP Models**

- **OSI Model:** A conceptual framework with seven layers (Physical, Data Link, Network, Transport, Session, Presentation, Application) that standardizes network functions.
- **TCP/IP Model:** A more practical model with four layers (Network Interface, Internet, Transport, Application) used for internet communications.

<h2 align=center>Practice: Networking Concepts</h2>

**Hands-on exercises to understand basic networking concepts**

1. **Viewing Network Interfaces:**
   ```bash
   ifconfig
   ```
   ```
   eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
           inet 192.168.1.2  netmask 255.255.255.0  broadcast 192.168.1.255
           ...
   ```

2. **Pinging a Website:**
   ```bash
   ping www.google.com
   ```
   ```
   PING www.google.com (172.217.14.196): 56 data bytes
   64 bytes from 172.217.14.196: icmp_seq=0 ttl=54 time=10.2 ms
   ```

<h2 align=center>Basic Network Configuration</h2>

**Understanding Network Interfaces**

Network interfaces are the points of connection between a computer and a network. Common interfaces include Ethernet (eth0, eth1) and wireless (wlan0).

**Configuring IP Addresses (Static and Dynamic)**

- **Static IP Configuration:**
  ```bash
  sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0
  ```
  ```
  eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
           inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
           ...
  ```

- **Dynamic IP Configuration (using DHCP):**
  ```bash
  sudo dhclient eth0
  ```
  ```
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
  DHCPOFFER from 192.168.1.1
  DHCPREQUEST on eth0 to 255.255.255.255 port 67
  DHCPACK from 192.168.1.1
  bound to 192.168.1.20 -- renewal in 3600 seconds.
  ```

**Network Masks and Gateways**

- **Setting a Network Mask:**
  ```bash
  sudo ifconfig eth0 netmask 255.255.255.0
  ```

- **Setting a Default Gateway:**
  ```bash
  sudo route add default gw 192.168.1.1
  ```

<h2 align=center>Validating Network Configuration</h2>

**Using ifconfig and ip Commands**

- **ifconfig:**
  ```bash
  ifconfig eth0
  ```
  ```
  eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
           inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
           ...
  ```

- **ip:**
  ```bash
  ip addr show eth0
  ```
  ```
  2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
      inet 192.168.1.10/24 brd 192.168.1.255 scope global eth0
         valid_lft forever preferred_lft forever
  ```

**Checking Network Connectivity with ping**

- **Ping Command:**
  ```bash
  ping 8.8.8.8
  ```
  ```
  PING 8.8.8.8 (8.8.8.8): 56 data bytes
  64 bytes from 8.8.8.8: icmp_seq=0 ttl=54 time=10.2 ms
  ```

**Verifying Routing Tables with route and ip route**

- **route:**
  ```bash
  route -n
  ```
  ```
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
  192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
  ```

- **ip route:**
  ```bash
  ip route show
  ```
  ```
  default via 192.168.1.1 dev eth0
  192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
  ```

<h2 align=center>Configuring Networking with nmcli</h2>

**Introduction to nmcli**

`nmcli` is a command-line tool for managing NetworkManager and reporting network status.

**Basic nmcli Commands**

- **Show Network Status:**
  ```bash
  nmcli general status
  ```
  ```
  STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN
  connected  full          enabled  enabled  enabled  enabled
  ```

- **List Network Connections:**
  ```bash
  nmcli connection show
  ```
  ```
  NAME                UUID                                  TYPE      DEVICE
  Wired connection 1  1c4e2d5e-3b6a-4f8e-9a5e-2b5e5e5e5e5e  ethernet  eth0
  ```

**Creating and Modifying Network Connections**

- **Create a New Connection:**
  ```bash
  nmcli connection add type ethernet ifname eth0 con-name my-eth0
  ```
  ```
  Connection 'my-eth0' (1c4e2d5e-3b6a-4f8e-9a5e-2b5e5e5e5e5e) successfully added.
  ```

- **Modify an Existing Connection:**
  ```bash
  nmcli connection modify my-eth0 ipv4.addresses 192.168.1.10/24
  ```
  ```
  Connection 'my-eth0' (1c4e2d5e-3b6a-4f8e-9a5e-2b5e5e5e5e5e) successfully modified.
  ```

<h2 align=center>Practice: Configuring Networking with nmcli</h2>

**Practical exercises using nmcli for network configuration**

1. **Activate a Connection:**
   ```bash
   nmcli connection up my-eth0
   ```
   ```
   Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/1)
   ```

2. **Deactivate a Connection:**
   ```bash
   nmcli connection down my-eth0
   ```
   ```
   Connection 'my-eth0' successfully deactivated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/1)
   ```

<h2 align=center>Editing Network Configuration Files</h2>

**Understanding Network Configuration Files (e.g., /etc/sysconfig/network-scripts/)**

Network configuration files store settings for network interfaces. In Red Hat-based systems, these files are located in `/etc/sysconfig/network-scripts/`.

**Editing Files with vi or nano**

- **Editing with vi:**
  ```bash
  vi /etc/sysconfig/network-scripts/ifcfg-eth0
  ```
  ```
  DEVICE=eth0
  BOOTPROTO=static
  IPADDR=192.168.1.10
  NETMASK=255.255.255.0
  GATEWAY=192.168.1.1
  ```

- **Editing with nano:**
  ```bash
  nano /etc/sysconfig/network-scripts/ifcfg-eth0
  ```
  ```
  DEVICE=eth0
  BOOTPROTO=static
  IPADDR=192.168.1.10
  NETMASK=255.255.255.0
  GATEWAY=192.168.1.1
  ```
  

**Applying Changes and Restarting Network Services**

- **Restarting Network Service:**
  ```bash
  sudo systemctl restart network
  ```
  ```
  Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe" for details.
  ```

<h2 align=center>Practice: Editing Network Configuration Files</h2>

**Hands-on practice editing and managing network configuration files**

1. **Editing a Configuration File:**
   ```bash
   sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
   ```
   ```
   DEVICE=eth0
   BOOTPROTO=static
   IPADDR=192.168.1.10
   NETMASK=255.255.255.0
   GATEWAY=192.168.1.1
   ```

2. **Restarting the Network Service:**
   ```bash
   sudo systemctl restart network
   ```
   ```
   Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe" for details.
   ```

<h2 align=center>Configuring Hostname and Name Resolution</h2>

**Setting the Hostname**

- **Temporarily Setting the Hostname:**
  ```bash
  sudo hostnamectl set-hostname myhostname
  ```
  ```
  ```

- **Permanently Setting the Hostname:**
  ```bash
  sudo vi /etc/hostname
  ```
  ```
  myhostname
  ```

**Configuring /etc/hosts for Local Name Resolution**

- **Editing /etc/hosts:**
  ```bash
  sudo vi /etc/hosts
  ```
  ```
  127.0.0.1   localhost
  127.0.1.1   myhostname
  ```

**Configuring DNS Servers in /etc/resolv.conf**

- **Editing /etc/resolv.conf:**
  ```bash
  sudo vi /etc/resolv.conf
  ```
  ```
  nameserver 8.8.8.8
  nameserver 8.8.4.4
  ```

<h2 align=center>Practice: Configuring Hostname and Name Resolution</h2>

**Practical exercises for hostname and DNS configuration**

1. **Setting the Hostname:**
   ```bash
   sudo hostnamectl set-hostname myhostname
   ```
   ```

2. **Editing /etc/hosts:**
   ```bash
   sudo vi /etc/hosts
   ```
   ```
   127.0.0.1   localhost
   127.0.1.1   myhostname
   ```

<h2 align=center>Introduction to Network Protocols</h2>

**Overview of Common Network Protocols (HTTP, FTP, SSH, etc.)**

- **HTTP (Hypertext Transfer Protocol):** Used for transferring web pages.
- **FTP (File Transfer Protocol):** Used for transferring files.
- **SSH (Secure Shell):** Used for secure remote login and command execution.

**Understanding TCP vs. UDP**

- **TCP (Transmission Control Protocol):** Connection-oriented protocol ensuring reliable data transfer.
- **UDP (User Datagram Protocol):** Connectionless protocol allowing faster, but less reliable, data transfer.

<h2 align=center>Understanding IP Addressing and Subnetting</h2>

**IPv4 and IPv6 Addressing**

- **IPv4 Addressing:** 32-bit addresses, e.g., 192.168.1.1
- **IPv6 Addressing:** 128-bit addresses, e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334

**Subnetting Basics and CIDR Notation**

- **Subnetting:** Dividing a network into smaller sub-networks.
- **CIDR (Classless Inter-Domain Routing) Notation:** A method for allocating IP addresses and routing, e.g., 192.168.1.0/24

**Calculating Subnets and Hosts**

- **Subnet Calculation Example:**
  ```bash
  ipcalc 192.168.1.0/24
  ```
  ```
  Address:   192.168.1.0          11000000.10101000.00000001. 00000000
  Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
  Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
  =>
  Network:   192.168.1.0/24       11000000.10101000.00000001. 00000000
  HostMin:   192.168.1.1          11000000.10101000.00000001. 00000001
  HostMax:   192.168.1.254        11000000.10101000.00000001. 11111110
  Broadcast: 192.168.1.255        11000000.10101000.00000001. 11111111
  Hosts/Net: 254                   Class C, Private Internet
  ```

<h2 align=center>Basic Network Troubleshooting</h2>

**Using ping, traceroute, and netstat**

- **ping:**
  ```bash
  ping 8.8.8.8
  ```
  ```
  PING 8.8.8.8 (8.8.8.8): 56 data bytes
  64 bytes from 8.8.8.8: icmp_seq=0 ttl=54 time=10.2 ms
  ```

- **traceroute:**
  ```bash
  traceroute www.google.com
  ```
  ```
  traceroute to www.google.com (172.217.14.196), 30 hops max, 60 byte packets
   1  192.168.1.1 (192.168.1.1)  1.123 ms  1.098 ms  1.073 ms
   2  10.0.0.1 (10.0.0.1)  2.123 ms  2.098 ms  2.073 ms
   ...
  ```

- **netstat:**
  ```bash
  netstat -tuln
  ```
  ```
  Active Internet connections (only servers)
  Proto Recv-Q Send-Q Local Address           Foreign Address         State
  tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
  udp        0      0 0.0.0.0:68              0.0.0.0:*               
  ```

**Diagnosing Common Network Issues**

- **Checking Interface Status:**
  ```bash
  ip link show eth0
  ```
  ```
  2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
      link/ether 00:1a:2b:3c:4d:5e brd ff:ff:ff:ff:ff:ff
  ```

**Understanding and Using tcpdump for Packet Analysis**

- **Capturing Packets:**
  ```bash
  sudo tcpdump -i eth0
  ```
  ```
  tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
  listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
  12:34:56.789123 IP 192.168.1.10.12345 > 8.8.8.8.53: 12345+ A? www.google.com. (32)
  ```

<h2 align=center>Lab: Managing Red Hat Enterprise Linux Networking</h2>

**Comprehensive lab exercises covering all the above topics**

1. **Configuring a Static IP Address:**
   ```bash
   sudo nmcli connection add type ethernet ifname eth0 con-name static-eth0 ip4 192.168.1.10/24 gw4 192.168.1.1
   ```
   ```
   Connection 'static-eth0' (1c4e2d5e-3b6a-4f8e-9a5e-2b5e5e5e5e5e) successfully added.
   ```

2. **Editing Network Configuration Files:**
   ```bash
   sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
   ```
   ```
   DEVICE=eth0
   BOOTPROTO=static
   IPADDR=192.168.1.10
   NETMASK=255.255.255.0
   GATEWAY=192.168.1.1
   ```

3. **Restarting Network Services:**
   ```bash
   sudo systemctl restart network
   ```
   ```

   Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe" for details.
   ```

4. **Using tcpdump for Packet Analysis:**
   ```bash
   sudo tcpdump -i eth0
   ```
   ```
   tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
   listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
   12:34:56.789123 IP 192.168.1.10.12345 > 8.8.8.8.53: 12345+ A? www.google.com. (32)
   ```

5. **Troubleshooting Network Issues:**
   ```bash
   sudo ip link set eth0 down
   sudo ip link set eth0 up
   ```
   ```
   2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
       link/ether 00:1a:2b:3c:4d:5e brd ff:ff:ff:ff:ff:ff
   ```

6. **Verifying DNS Configuration:**
   ```bash
   cat /etc/resolv.conf
   ```
   ```
   nameserver 8.8.8.8
   nameserver 8.8.4.4
   ```

7. **Checking Routing Table:**
   ```bash
   ip route show
   ```
   ```
   default via 192.168.1.1 dev eth0
   192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
   ```

<h2 align=center>Lab: Managing Red Hat Enterprise Linux Networking</h2>

**Comprehensive lab exercises covering all the above topics**

1. **Configuring a Static IP Address:**
   ```bash
   sudo nmcli connection add type ethernet ifname eth0 con-name static-eth0 ip4 192.168.1.10/24 gw4 192.168.1.1
   ```
   ```
   Connection 'static-eth0' (1c4e2d5e-3b6a-4f8e-9a5e-2b5e5e5e5e5e) successfully added.
   ```

2. **Editing Network Configuration Files:**
   ```bash
   sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
   ```
   ```
   DEVICE=eth0
   BOOTPROTO=static
   IPADDR=192.168.1.10
   NETMASK=255.255.255.0
   GATEWAY=192.168.1.1
   ```

3. **Restarting Network Services:**
   ```bash
   sudo systemctl restart network
   ```
   ```
   Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe" for details.
   ```

4. **Using tcpdump for Packet Analysis:**
   ```bash
   sudo tcpdump -i eth0
   ```
   ```
   tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
   listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
   12:34:56.789123 IP 192.168.1.10.12345 > 8.8.8.8.53: 12345+ A? www.google.com. (32)
   ```

5. **Troubleshooting Network Issues:**
   ```bash
   sudo ip link set eth0 down
   sudo ip link set eth0 up
   ```
   ```
   2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
       link/ether 00:1a:2b:3c:4d:5e brd ff:ff:ff:ff:ff:ff
   ```

6. **Verifying DNS Configuration:**
   ```bash
   cat /etc/resolv.conf
   ```
   ```
   nameserver 8.8.8.8
   nameserver 8.8.4.4
   ```

7. **Checking Routing Table:**
   ```bash
   ip route show
   ```
   ```
   default via 192.168.1.1 dev eth0
   192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
   ```

<h2 align=center>Real-world Scenarios and Troubleshooting</h2>

**Scenario 1: Network Interface Not Coming Up**

- **Symptom:** The network interface `eth0` is not coming up after a reboot.
- **Solution:**
  ```bash
  sudo ip link set eth0 up
  ```
  ```
  2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
      link/ether 00:1a:2b:3c:4d:5e brd ff:ff:ff:ff:ff:ff
  ```

**Scenario 2: DNS Resolution Issues**

- **Symptom:** Unable to resolve domain names.
- **Solution:**
  ```bash
  cat /etc/resolv.conf
  ```
  ```
  nameserver 8.8.8.8
  nameserver 8.8.4.4
  ```
  Ensure the DNS servers are correctly configured.

**Scenario 3: Network Connectivity Issues**

- **Symptom:** Unable to connect to the internet.
- **Solution:**
  ```bash
  ping 8.8.8.8
  ```
  ```
  PING 8.8.8.8 (8.8.8.8): 56 data bytes
  64 bytes from 8.8.8.8: icmp_seq=0 ttl=54 time=10.2 ms
  ```
  If the ping fails, check the default gateway:
  ```bash
  ip route show
  ```
  ```
  default via 192.168.1.1 dev eth0
  192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
  ```

**Scenario 4: Packet Loss**

- **Symptom:** Experiencing packet loss.
- **Solution:**
  ```bash
  sudo tcpdump -i eth0
  ```
  ```
  tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
  listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
  12:34:56.789123 IP 192.168.1.10.12345 > 8.8.8.8.53: 12345+ A? www.google.com. (32)
  ```
  Analyze the captured packets to identify the source of packet loss.
