### **Basic Router Configuration**

- **`Router(config)#hostname A`**: Provide hostname for the router 
- **`A(config)#enable secret (password) `**
- **`A(config)#line con 0 / aux 0 / vty 0 4 `**
- **`A(config)#password (password) `**
- **`A(config)#login - A(config)#exit`** 
- **`A(config)#interface (id like g0/0) `**
- **`A(config-f)#no shut `**
- **`A(config-f)#ip address (ip) (subnet mask) `**
- **`A(config-f)#exit`**

### **Monitoring Commands**

- **`A#show version`**: Displays the system version, configuration register value, and other details. The default configuration register value is typically `0x2102`.
- **`A#show flash`**: Lists the contents of the flash memory.
- **`A#show running-config`**: Shows the current running configuration.
- **`show startup-config`**: Displays the startup configuration stored in NVRAM.
- **`A#show ip int`**: Displays all IP parameters for the interfaces.
- **`A#show ip int brief`**: A concise version showing key parameters in a horizontal format. Often favored for quick checks.
- **`A#show protocols`**: Displays the status of protocols configured on router or switch interfaces.

### **Miscellaneous**

- **`copy running-config startup-config`**: use to save the starting configuration to NVRAM.
- **`service password-encryption`**: encryption for passwords.
- **`telnet <IP-address>`**: Initiates a Telnet session to the specified router IP.


---

### **CDP (Cisco Discovery Protocol) Configuration Commands**:

- **`cdp run`**: Enables CDP globally on the device.
- **`cdp timer [seconds]`**: Configures the CDP advertisement timer (in seconds).
- **`cdp holdtime [seconds]`**: Sets the CDP hold time (the time a device retains neighbor information).
- **`cdp enable`**: Enables CDP on a specific interface.
- **`no cdp enable`**: Disables CDP on a specific interface.
- **`show cdp`**: Displays global CDP status information.
- **`show cdp neighbors`**: Lists all CDP-discovered neighbors with basic information.
- **`show cdp neighbors detail`**: Provides detailed information about CDP neighbors, including IP addresses and capabilities.
- **`no cdp run`**: Disables CDP globally on the device.

--- 

### **Static IP Hosting**

- `A(config)# ip host B 172.16.20.2 `:This command maps the name to the respective IP address.
- **Limitations:** You can configure up to **8 static hosts** using this method. This is useful to remember the IPs of frequently accessed routers.

### **Dynamic IP Hosting**

- **`A(config)# ip domain-lookup`**: Enables DNS-based hostname resolution (default is enabled).
- **`A(config)# no ip domain-lookup`**: Disables DNS-based hostname resolution.
- **`A(config)# ip domain-name [domain-name]`**: Defines the default DNS domain name for the router.
- **`A(config)# ip name-server [DNS-server-IP]`**: Specifies the DNS server IP address for name resolution.
- **`A(config)# ip domain-list [domain-name]`**: Adds a domain name to the DNS search list.
- **`A(config)# ip host [hostname] [IP-address]`**: Manually maps a hostname to an IP address in the router's host table.
- **`A# ping [hostname]`**: Resolves the hostname via DNS and pings the mapped IP address.
- **`A# show hosts`**: Displays a cached list of hostnames and their corresponding IP addresses.

---

### **Routing**
#### Static Routes

* **`A(config)# ip route [destination-network] [subnet-mask] [next-hop-address]`**: Configures a static route to a specified destination network through a next-hop IP address.

#### Default Routes

 - **`A(config)# ip route 0.0.0.0 0.0.0.0 [next-hop-address]`**: Configures a default route to forward all unspecified traffic to the next-hop IP address.

#### Exit Interface

- **`A(config)# ip route [destination-network] [subnet-mask] [exit-interface]`**: Configures a static route to a specified destination network using an exit interface instead of a next-hop address.

---

### **Router Information Protocol (RIP)**

- **`A(config)# router rip`**: Enters RIP routing configuration mode.
- **`A(config-router)# version [1|2]`**: Sets the RIP version to use (1 or 2).
- **`A(config-router)# network [classfull network-address]`**: Specifies the networks to advertise via RIP.
- **`A(config-router)# passive-interface [interface]`**: Prevents RIP updates from being sent on the specified interface while still receiving updates.
- **`A(config-router)# no passive-interface [interface]`**: Enables RIP updates on the specified interface.
- **`A# show ip rip database`**: Shows the contents of the RIP routing database.

---

### **OSPF (Open Shortest Path First)**

- **`A(config)# router ospf [process-id]`**: Enters OSPF routing configuration mode with the specified process ID.
- **`A(config-router)# network [network-address] [wildcard-mask] area [area-id]`**: Defines OSPF networks and associates them with a specific area.
- **`A(config-router)# passive-interface [interface]`**: Prevents OSPF updates from being sent on the specified interface while still receiving updates.
- **`A(config-router)# no passive-interface [interface]`**: Enables OSPF updates on the specified interface.
- **`A# show ip ospf`**: Displays OSPF process information and parameters.
- **`A# show ip ospf neighbor`**: Lists OSPF neighbors and their states.
- **`A# show ip ospf database`**: Shows the OSPF link-state database, including LSAs.

---

### **Loopback**

- **`A(config)# interface loopback [interface-number]`**: Enters configuration mode for a specified loopback interface.
- **`A(config-if)# ip address [ip-address] [255.255.255.255]`**: Assigns an IP address and subnet mask to the loopback interface.
- **`A(config-if)# no shutdown`**: Activates the loopback interface (though it is usually up by default).
- **`A(config-if)# exit`**: Exits loopback interface configuration mode back to global configuration mode.
- **`A# show running-config interface loopback [interface-number]`**: Shows the current configuration for a specific loopback interface.
- **`A# show ip interface brief`**: Displays a summary of all interfaces, including loopback interfaces and their statuses.

---

### **EIGRP (Enhanced Interior Gateway Routing Protocol)**

- **`A(config)# router eigrp [autonomous-system-number]`**: Enters EIGRP routing configuration mode for the specified autonomous system (AS).
- **`A(config-router)# network [network-address]`**: Specifies the networks to include in EIGRP routing updates.
- **`A(config-router)# no auto-summary`**: Disables automatic summarization of routes in EIGRP. This is on by default.
- **`A(config-router)# passive-interface [interface]`**: Prevents EIGRP updates from being sent on the specified interface while still receiving updates.
- **`A(config-router)# no passive-interface [interface]`**: Enables EIGRP updates on the specified interface.
- **`A# show ip eigrp neighbors`**: Displays the EIGRP neighbor table, listing directly connected EIGRP routers.
- **`A# show ip eigrp topology`**: Displays the EIGRP topology table, showing all known routes, including their feasible distances and reported distances.
- **`A# show ip route eigrp`**: Shows the EIGRP routes in the routing table.

---

### **Access Control Lists (ACL)**

#### Standard ACLs

 - **`A(config)# access-list [number] [permit|deny] [source]`**: Creates a standard ACL rule to permit or deny traffic based on the source IP address.
 - **`A# show access-lists`**: Displays all configured ACLs and their rules.
 - **`A(config)# no access-list [number]`**: Deletes the specified standard ACL.

#### Extended ACLs

- **`A(config)# access-list [number] [permit|deny] [protocol] [source] [source-wildcard] [destination] [destination-wildcard]`**: Creates an extended ACL rule specifying the protocol, source, and destination IP addresses.
- **`A(config)# no access-list [number] [line-number]`**: Deletes a specific line from an existing ACL.
-**`A(config)# access-list 10 permit 172.16.10.10 0.0.0.255`**-wildcard
-**`A(config)# access-list 10 permit 172.16.10.10 0.0.0.0`**

#### Applying ACLs

- **`A(config)# interface [interface-type] [interface-number]`**: Enters interface configuration mode where the ACL will be applied.
- **`A(config-if)# ip access-group [number] [in|out]`**: Applies the specified ACL to the interface in the inbound or outbound direction.

#### Others:

- `A(config)# access-list 100 permit ip any any`: permit all traffic
- `A(config)# access-list 100 deny ip any any`: deny all traffic

---

### **CHAP(Challenge Handshake Authentication Protocol) Configuration**

1. **`A(config)# interface [interface-type] [interface-number]`**: Enters interface configuration mode for the specified interface.
2. **`A(config-if)# ppp chap hostname [username]`**: Configures the username for CHAP authentication.
3. **`A(config-if)# ppp chap password [password]`**: Sets the password for CHAP authentication.
4. **`A(config-if)# encapsulation ppp`**: Enables PPP encapsulation on the interface, necessary for using CHAP.

### **PAP(Password Authentication Protocol) Configuration**

5. **`A(config-if)# ppp pap sent-username [username] password [password]`**: Configures the username and password for PAP authentication.
6. **`A(config-if)# encapsulation ppp`**: (Same as CHAP) Enables PPP encapsulation on the interface for PAP use.

---
### **NAT (Network Address Translation)**

#### **Static**

Here the LAN side should be `inside` and WAN side as `outside`:

**`A(config)#int g0/0 `**
**`A(config-if)#ip nat inside`**

**`A(config)#int g0/1`** 
**`A(config-if)#ip nat outside`**

**`A(config)#ip nat inside source static 172.16.10.2 202.208.220.2`**: Mapping the private IP with the public IP.

#### **Dynamic**

- Enter global configuration mode:
	**`A# configure terminal`**

- Configure the inside interface (where internal traffic enters the router):
	**`A(config)# interface GigabitEthernet0/1`**
	**`A(config-if)# ip nat inside`**
	**`A(config-if)# exit`**

- Configure the outside interface (where external traffic enters the router):
	**`A(config)# interface GigabitEthernet0/2`**
	**`A(config-if)# ip nat outside`**
	**`A(config-if)# exit`**

- Create an access list to permit internal IP range (e.g., 192.168.1.0/24):
	**`A(config)# access-list 1 permit 192.168.1.0 0.0.0.255`**

- Define a NAT pool for the external IP range (e.g., 203.0.113.1 to 203.0.113.10):
	**`A(config)# ip nat pool MY_POOL 203.0.113.1 203.0.113.10 netmask 255.255.255.0`**

 - Bind the ACL to the NAT pool, enabling dynamic NAT for the specified internal network:
	**`A(config)# ip nat inside source list 1 pool MY_POOL`**

- Save the configuration to prevent loss after reboot:
	**`A(config)# exit`**

#### **Dynamic with Overload**

While binding the ACL to the NAT pool, use the `overload keyword`:
**`A(config)# ip nat inside source list 1 pool MY_POOL overload
OR
`A(config)# ip nat inside source list 1 interface GigabitEthernet0/2 overload`

#### **VTP**
**`A(config)# vtp domain sunbeam`**
**`A(config)# vtp mode server`**
**`A(config)# vtp mode client`**
**`A(config)# vtp mode transport`** / transparent
**`A(config)# vtp password password`**

**`A# show vlan`**
**`A# show vlan brief`**
**`A# show int trunk`**
**`A# show mac address-table`**
**`A# show vtp status`**

**`A(config)# int f1/1`**
**`A(config-if)# switchport access vlan 2`**
or
**`A(config)# int range f1/1 - 8 `**
**`A(config-range-if)# switchport access vlan 2`**

#### **Switch**
**`A(config)# vlan 2`**
**`A(config-vlan)# name sales`**
**`A(config)# exit`**
**`A(config)# vlan 3`**
**`A(config-vlan)# name mktg`**
**`A(config)# exit`**

**`A(config)# int f1/1`**
**`A(config-if)# switchport access vlan 2`**
or
**`A(config)# int range f1/1 - 8 `**
**`A(config-range-if)# switchport access vlan 2`**

**`A(config)# int g0/0`**
**`A(config-if)# switchport mode trunk`**
**`A(config-if)# switchport trunk incapsulation isl`**
**`A(config-if)# switchport trunk incapsulation dot.iq [vlan no.]`**
---


### **Configuration for VLAN1 (Step-wise)**
- **`switch> on`**: 
- **`switch# conf t`**: Enters global configuration mode.
- **`switch(config)# int vlan1`**: Enters configuration mode for VLAN 1.
- **`switch(config-if)# no shutdown`**: Activates the VLAN interface.
- **`switch(config-if)# ip address 172.16.100.10 255.255.255.0`**: Assigns an IP address to VLAN 1.
- **`switch(config-if)# exit`**: Exits the VLAN configuration mode. Correct.
- **`switch(config)# ip default-gateway 172.16.10.1`**: Sets the default gateway for the switch.
- **`switch(config)# int fa1/0`**: Enters configuration mode for FastEthernet interface 1/0.
- **`switch(config-if)# switchport port-security mac-address <MAC address>`**: Here, instead of the actual MAC address, we can also use `sticky`. This states that the PC's MAC address will be made permanent here. `sticky` is a keyword.
- **`switch(config-if)# switchport port-security violation shutdown`**: Configures the switch to shut down the port if a violation occurs.

---

### **Configuration of Multiple Ports at Once**

**`switch(config)# int range f0/1 - n`**: Enters configuration mode for a range of FastEthernet interfaces (from fa0/1 to fa0/n) to apply settings simultaneously.

---

### **Configuration for VLANs**

- **`switch# conf t`**: Enters global configuration mode.
- **`switch(config)# vlan [vlan-id]`**: Creates a new VLAN with the specified VLAN ID.
- **`switch(config-vlan)# name [vlan-name]`**: Assigns a name to the newly created VLAN for identification.
- **`switch(config)# interface vlan [vlan-id]`**: Enters configuration mode for the VLAN interface.
- **`switch(config-if)# ip address [ip-address] [subnet-mask]`**: Assigns an IP address and subnet mask to the VLAN interface.
- **`switch(config-if)# no shutdown`**: Activates the VLAN interface.
- **`switch(config-if)# exit`**: Exits VLAN interface configuration mode back to global configuration mode.
- **`switch(config)# interface [interface-type] [interface-number]`**: Enters configuration mode for a switch port to assign it to the new VLAN.
  or
  **`switch(config)# interface range f0/1 - n`**
- **`switch(config-if)# switchport access vlan [vlan-id]`**: Assigns the switch port to the newly created VLAN.

---

### **Declaring Trunks**

- **`switch(config)# int g0/0`**: Enters configuration mode for GigabitEthernet interface 0/0.
- **`switch(config)# switchport mode trunk`**: Configures the interface as a trunk port.
- **`switch(config)# switchport trunk encapsulation dot1q`**: Configures the trunk port to use 802.1Q for VLAN tagging.

---

### **VTP (VLAN Trunking Protocol)**

- **`A# conf t`**: Enters global configuration mode.
- **`A(config)# vtp domain [domain-name]`**: Configures the VTP domain name for VLAN information sharing.
- **`A(config)# vtp mode [server|client|transparent]`**: Sets the VTP mode for the switch (server, client, or transparent).
- **`A(config)# vtp password [password]`**: Sets the VTP password for authentication between switches.
- **`A(config)# interface [interface-type] [interface-number]`**: Enters interface configuration mode for trunk settings.
- **`A(config-if)# switchport mode trunk`**: Configures the interface as a trunk to carry VLAN information.
- **`A# show vtp status`**: Displays the current VTP status, including the VTP mode and revision number.

---

### **Sub Interfaces**

- **`A# conf t`**: Enters global configuration mode.
- **`A(config)# interface [interface-type] [interface-number].[subinterface-number]`**: Creates a sub-interface for the specified physical interface.
- **`A(config-subif)# encapsulation dot1q [vlan-id]`**: Configures 802.1Q encapsulation for the sub-interface, specifying the VLAN ID.
- **`A(config-subif)# ip address [ip-address] [subnet-mask]`**: Assigns an IP address and subnet mask to the sub-interface.
- **`A(config-subif)# no shutdown`**: Activates the sub-interface.

---

### **Monitoring Commands**

- **`show vlan`**: Displays detailed information about all configured VLANs on the switch.
- **`show vlan brief`**: Provides a summary of VLANs, including their IDs and names.
- **`show int trunk`**: Shows trunk interfaces and their VLAN membership and status.
- **`show mac-address table`**: Displays MAC addresses learned on the switch ports along with their corresponding VLANs.
- **`show vtp status`**: Displays the VTP status, including mode, domain name, and revision number of the switch.