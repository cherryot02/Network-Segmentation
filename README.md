# Network Configuration and ACLs.
The main purpose of this lab is to learn how to set and configure IP addresses on different network devices such as router and switches, as well as workstations and one server;
then verify their connectivity by pinging and seeing no reds or errors on the connections.<br /> <br />
I used Cisco Packet Tracer in order to perform the tasks. <br />

Given a topology, I had to create a similar topology of the following image. 
![image 1a-Basis](https://github.com/user-attachments/assets/c36881d2-15f7-4bcf-a2f5-b8bdf774e5b0)

## Task 1
Open Cisco Packet Tracer and on the logical tab, set-up the devices and cables by dragging the tools from the bottom right of the screen.<br />
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
What we are doing here is that, we are trying to make sure the right cables are connected and beging given a specific address and no shut means that the port is open. <br />
There are tendencies that the ports is not turned on leading to no connectivity.

