## What is Iptables, and How Does It Work?
Simply put, iptables is a firewall program for Linux. It will monitor traffic from and to your server
using tables. These tables contain sets of rules, called chains, that will filter incoming and
outgoing data packets.

### Syntax
```
sudo iptables <option> <chain> -i <interface> -p <protocol> -s <source> --dport <destination port> -m <match> -j <target>
```
#### Option : -
  * **-A** Add one or more rules to the end of the selected chain.
  * **-D** Delete one or more rules from the selected chain.
  * **-I** Insert one or more rules into the selected chain as the given rule number
  
#### Chain : -
  In this iptables tutorial, we are going to work with one of the default
  tables, called filter. It consists of three chains:
  * **INPUT (Inbound)** – controls incoming packets to the server.
  * **FORWARD** – filters incoming packets that will be forwarded somewhere else.
  * **OUTPUT (Outbound)** – filter packets that are going out from your server.
  
#### Interface : -
  the network interface whose traffic you want to filter, such as eth0, lo,
  ppp0, etc.
  
#### Protocol : -
  the network protocol where your filtering process takes place. It can be
  either tcp, udp, udplite, icmp, sctp, icmpv6, and so on. Alternatively,
  you can type all to choose every protocol.
  
#### Source : -
  the address from which traffic comes from. You can add a hostname or IP
  address.
  
#### Destination port : -
  the destination port number of a protocol, such as 22 (SSH), 443 (https),
  etc.
  
#### Match : -
  Match the specified option. Here have many option like comment, iprange

#### Target : -
  When a packet matches a rule, it is given a target, which can be another
  chain or one of these special values:
  * **ACCEPT** – will allow the packet to pass through.
  * **DROP** – will not let the packet pass through.
  * **RETURN** – stops the packet from traversing through a chain and tell it to go back to the previous chain.


To get the latest rule status on your server, please enter below command:
```
  sudo iptables -L
```

### Example

1.Open a 8080 port for incoming request
```
sudo iptables -I INPUT -p tcp --dport 8080 -m comment --comment "8080" -j ACCEPT
```
2.Delete this chain rule
```
sudo iptables -D INPUT -p tcp --dport 8080 -m comment --comment "8080" -j ACCEPT
```
3.Delete this chain rule using line number
  * First - find line numbers using this command
  ```
  sudo iptables -L --line-numbers
  ```
  * Then - Use those line number which you want to delete
  ```
  sudo iptables -D INPUT 4
  ```
4.Open all port for incoming request
```
sudo iptables -I INPUT -m comment --comment "open all port" -j ACCEPT
```
