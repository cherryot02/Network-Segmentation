# Network Configuration and ACLs.
The main purpose of this lab is to learn how to set and configure IP addresses on different network devices such as router and switches, as well as workstations and one server;
then verify their connectivity by pinging and seeing no reds or errors on the connections.<br /> <br />
I used Cisco Packet Tracer in order to perform the tasks. <br />

Given a topology, I had to create a similar topology of the following image. 
![image 1a-Basis](https://github.com/user-attachments/assets/c36881d2-15f7-4bcf-a2f5-b8bdf774e5b0)

## Task 1 - setting up
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

## Task 2 - Router CLI 
Use routing method called RIP, exceute the following commands on Router1 (R1)
```
Router1( config)# router rip 
Router1( config-router)# network 192.168.0.0 
Router1( config-router)# network 10.0.0.0
Router1( config-router)# exit 
Router1( config)#
```
## Task 3 - Router 2 and other devices
Do the same thing in Router2 but used the following commands. 
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
Image3

Then by following the given topology, configure the IP addresses of PC0, PC1, and Server.

## Task 4 - Standard ACL configuration

Let’s see how to configure Standard ACL. In this demonstration, we will restrict host 10.0.0.2 from accessing Router2. To do so, perform the following steps:
1.  First, execute the following command to deny host 10.0.0.2.
```
Router2( config)# access-list 10 deny host 10.0.0.2
```
2.  Once you deny a host on a router, the router will deny all the hosts until you explicitly define the permitted hosts. In the following command, we will permit all the hosts.
```
Router2( config)# access-list 10 permit any
```
3.  Next, switch to the interface on which you want to apply the ACL, in this case Fa0/ 1, and define the direction (inbound or outbound) of traffic that you want to filter. In this case, we will filter the incoming packets towards Router2. To do so execute the following commands.
```
Router2( config)# int fa0/ 1 
Router2( config-if)# ip access-group 10 in 
Router2( config-if)# exit 
Router2( config)# exit
```
4.  Once you applied an ACL on a router, execute the following command to view the applied ACLs.
```
Router2# show ip access-lists
 ```
5.  Next, open the Command Prompt of PC0, try to ping 192.168.0.2, you should not be able to ping, as shown in the following figure.


6.  Now, you have tested your ACL configuration. Now, remove the ACL configuration so the next exercise can be performed. To remove the configured ACL, execute the following command on Router2.
```
Router2( config)# no access-list 10 deny host 10.0.0.2
```
7.  Try to ping again from PC0 to Router2, this time you should be able to ping successfully because you have removed the applied ACL.

Results: <br />
I am including some of my ping where I got stuck at #6 pinging the server just so you know I did it. I was rechecking if I did the instructions right, turns out my router 2 network wasn’t configured, which I thought I did: fixed that. Then, also fixed my server’s IP addresses and default gateway because they were interchanged. So midway of pinging I realized it and fixed it, that’s why there’s a sudden packet that was received. Then the next pings worked.

![image](https://github.com/user-attachments/assets/b416539e-0d72-434a-bf2a-3ac367b37254)
![image](https://github.com/user-attachments/assets/6fa3cebe-73c6-4c0d-b5bb-28f4c722e431)
<br />
And everything for the ACLs worked as well.<br />
![image](https://github.com/user-attachments/assets/1c6f8752-6b2c-434b-982d-486cc6f39bc7)

# END
This marks the end of the lab. Some photos are yet to be uploaded.
