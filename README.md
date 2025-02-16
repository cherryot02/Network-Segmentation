# Network Configuration and ACLs.
The main purpose of this lab is to learn how to set and configure IP addresses on different network devices such as router and switches, as well as workstations and one server;
then verify their connectivity by pinging and seeing no reds or errors on the connections.<br /> <br />
I used Cisco Packet Tracer in order to perform the tasks. <br />

Given a topology, I had to create a similar topology of the following image. 
![image 1a-Basis](https://github.com/user-attachments/assets/c36881d2-15f7-4bcf-a2f5-b8bdf774e5b0)

## Task 1
Open Cisco Packet Tracer and on the logical tab, set-up the devices and ethernet cables by dragging the tools from the bottom right of the screen.<br />
Once you have created the preceding topology, configure the appropriate IP addresses as mentioned in the topology. 

image2

We have to execute the following commands on Router1:
```
Router 1> enable
Router 1# configure terminal
Router1( config)# int fa0/ 0 
Router1( config-if)# ip add 10.0.0.1 255.0.0.0 
Router1( config-if)# no shut 
Router1( config-if)# exit 

Router1( config)# int fa0/ 1 
Router1( config-if)# ip add 192.168.0.1 255.255.255.0 
Router1( config-if)# no shut 
Router1( config-if)# exit

```
What we are doing here is that, we are trying to make sure the right cables are connected, given a specific address, subnet masks and no shut means that the port stays open.
There are tendencies that the ports is not turned on leading to no connectivity.

## Task 2
Use routing method called RIP, exceute the following commands on Router1 (R1)
```
Router1( config)# router rip 
Router1( config-router)# network 192.168.0.0 
Router1( config-router)# network 10.0.0.0
Router1( config-router)# exit 
Router1( config)#
```
## Task 3
Do the same thing in Router2 but used the following commands
```
Router 2> enable
Router 2# configure terminal
Router2( config)# int fa0/ 0 
Router2( config-if)# ip add 20.0.0.1 255.0.0.0
Router2( config-if)# no shut 
Router2( config-if)# exit 

Router2( config)# int fa0/ 1 
Router2( config-if)# ip add 192.168.0.2 255.255.255.0 
Router2( config-if)# no shut 
Router2( config-if)# exit 

Router2( config)# router rip 
Router2( config-router)# network 192.168.0.0 
Router2( config-router)# network 20.0.0.0 
Router2( config-router)# exit

```
