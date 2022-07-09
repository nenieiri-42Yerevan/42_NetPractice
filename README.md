# NetPractice
## Solutions
### Level 1
For two or more computers to communicate, they need to be in the same network (i.e. their network addresses need to be the same). Otherwise, if their network addresses differ, a router will be needed.
#### Goal 1
Here, for Goal 1 there isn't a router and the computers are connected to each other directly.
In addition, we know the ip address and network mask of client B so we can easily calculate its network address, which will be equal to __104.95.23.0__:
```sh
IP Address:     104.95.23.12        |   01101000.01011111.00010111.00001100
Net-mask:       255.255.255.0 = 24  |   11111111.11111111.11111111.|00000000
                                        & (Bitwise and)
Network:        104.95.23.0/24      |   01101000.01011111.00010111.|00000000
```
This means that client A must also have the same network address: __104.95.23.0__. 
Network mask __255.255.255.0__ shows that in this network we can have `2^8 - 2 = 254` hosts (computers).
Where the smallest one will have the following address:
```
HostMin:        104.95.23.1         |	01101000.01011111.00010111.00000001
```
and the biggest:
```sh
HostMax:        104.95.23.254       |	01101000.01011111.00010111.11111110
```
The client B's IP address is 104.95.23.12, so we can choose any IP from the hosts' range except for 12. For example, if I choose 13 then client A's IP address will be:
```
Client A's Host: 104.95.23.13       |   01101000.01011111.00010111.00001101
```
So __104.95.23.13__ is one of the correct answers.<br>
Summing up, we can say that correct answers' range is __(104.95.23.1 - 104.95.23.254)__, except for 104.95.23.12.
#### Goal 2
This is the same as for Goal 1.
From Client C we get Network address which is __211.191.0.0__:
```sh
IP Address:     211.191.185.75      |   11010011.10111111.10111001.01001011
Net-mask:       255.255.0.0 = 16    |   11111111.11111111.|00000000.00000000
                                        & (Bitwise and)
Network:        211.191.0.0/16      |   11010011.10111111.|00000000.00000000
```
Client D has 255.255.0.0 Network Mask which means that this network can have `2^16 - 2 = 65,534` hosts.
Where the smallest one will have the following address:
```
HostMin:        211.191.0.1         |   011010011.10111111 .00000000.00000001
```
and the biggest:
```sh
HostMax:        211.191.255.254     |   11010011.10111111 .11111111.11111110
```
The client C’s IP address is 211.191.185.75, so we can choose any IP from the hosts’ range except for that. For example, if I choose 185.78 then client D’s IP address will be:
```
Client D's IP:  211.191.185.78      |   11010011.10111111.10111001.01001110
```
So __211.191.185.78__ is one of the correct answers.
Summing up, we can say that correct answers' range is __(211.191.0.1 - 211.191.255.254)__, except for 211.191.185.75.

![NetPractice - level 1](./imgs/level_1.png)
___
### Level 2
#### Goal 2
Here, our two computers have the same Network mask (255.255.255.252 and /30 are identical):
```sh
Network mask: 255.255.255.252 = 30  |   11111111.11111111.11111111.111111|00
```
The hosts' count will be `2^2 - 2 = 2`.<br>
For communication between two computers we need to choose any network address and calculate their IP addresses with help of our Network mask.<br>
We can choose any network address except for reserved addresses which lists you can see [__here__](https://en.wikipedia.org/wiki/Reserved_IP_addresses).
For example you can't use 127.0.0.1 because it is reserved.<br>
Here I choose __128.0.0.160__ Network address:
```sh
Network:        128.0.0.160/30      |   10000000.00000000.00000000.101000|00
```
In this case our hosts range will be `128.0.0.161 - 128.0.0.162`. <br>
Because, our network has only two computers and our hosts range also has two hosts, we have no other choice than the following:<br>
a computer:
```sh
IP Address:     128.0.0.161         |   10000000.00000000.00000000.10100001
```
and the other computer:
```sh
IP Address:     128.0.0.162         |   10000000.00000000.00000000.10100010
```
Thus our IP addresses in these network are __128.0.0.161__ and __128.0.0.162__.<br>

![NetPractice - level 2](./imgs/level_2.png)
___
### Level 3
#### Goal 1, Goal 2, Goal 3
There are 3 computers which are connected to each other through Switch.<br>
There is no router, which means that for comunication computers need to have the same network address, the same Net-mask, but different Host numbers.<br>
So, the Net-mask for A and B will be 255.255.255.128 (or /25).<br>
We also know the IP address of computer A. Therefore, we can calculate the network address of this subnet and its hosts' range.<br>
The Network address will be:
```sh
IP Address:     104.198.10.125      |   01101000.11000110.00001010.01111101
Net-mask:       255.255.255.128 = 25|   11111111.11111111.11111111.1|0000000
                                        & (Bitwise and)
Network:        104.198.10.0/25     |   01101000.11000110.00001010.0|0000000
```
Hosts' range will be `104.198.10.1 - 104.198.10.126`.<br>
So for computer B and C we can choose any host number from this range.<br>
Here I have chosen `104.198.10.123` and `104.198.10.124`.<br><br>
![NetPractice - level 3](./imgs/level_3.png)
___
### Level 4
___
### Level 5
Here there are two subnets, one of them start from Router R1 Interface and other from Router R2 Interface.
#### Goal 1
The Goal 1 is similar as level 1. Here we have IP address and Net-mask of Router R1 Interface so we can calculate the Network address and hosts' range of this subnet:
```sh
IP Address:     96.160.137.126      |   01100000.10100000.10001001.01111110
Net-mask:       255.255.255.128 = 25|   11111111.11111111.11111111.1|0000000
                                        & (Bitwise and)
Network:        96.160.137.0/25     |   01100000.10100000.10001001.0|0000000
```
Hosts' range will be `96.160.137.1 - 96.160.137.126`.<br>
So for computer A we can choose any host number from this range.<br>
Here I have chosen `96.160.137.125`.<br>
Net-mask of Computer A must be the same as Net-mask of Router R1: `255.255.255.128`.
#### Goal 2
This is a identical as Goal 1. So for this subnet we get hosts' range `138.127.64.1 - 138.127.127.254`.<br>
From this range I have chosen `138.127.80.80` IP for computer B. Its Net-mask will be the same as Net-mask for Router R2: `255.255.192.0` (This is the same as `/18`).
#### Goal 3
For communication between two computers which are in different subnets we need to configure their routing tables.<br>
A routing table contains the information necessary to forward a packet along the best path toward its destination.<br>
In routing tables we need to write where to pass packets that have some IPs in their destination which is out of subnet.<br>
Here we can just write that whole packets that does not match any IPs in this subnet pass to the router. In other words we define the `default` gateway for them (`default` is the same as `0.0.0.0/0`).<br>
So for computer A it will be the interface of Router R1 Interface`0.0.0.0/0=> 96.160.137.126`.<br>
And for computer B it will be the interface of Router R2 Interface`default => 138.127.118.254`.<br><br>
![NetPractice - level 5](./imgs/level_5.png)
___
### Level 6
___
### Level 7
___
### Level 8
On the level 8, first of all we need to check that on the routing table "internet I" there is only one record which is `149.248.202.0/26`. According to goals 2 and 3 our computers need to be connected to that internet, therefore we can assume that all our computers' IPs need to be in that subnet. So first of all we need to calculate the Network address and its host range:
```sh
IP Address:     149.248.202.0/26    |   10010101.11111000.11001010.00000000
Net-mask:       255.255.255.192     |   11111111.11111111.11111111.11|000000
                                        & (Bitwise and)
Network:        149.248.202.0       |   10010101.11111000.11001010.00|000000
```
Having Net-mask we can also calculate the number of valid hosts which will be `2^6 - 2 = 62`.<br> This means that we can have only `62` hosts. Where:
```
HostMin:        149.248.202.1       |   10010101.11111000.11001010.00000001
```
```sh
HostMax:        149.248.202.62      |   10010101.11111000.11001010.00111110
```
Now let's start from the Goal 1.
#### Goal 1
From the Interface D1 we can see that a part of our network (starting from R23 Interface) has a 255.255.255.240 (or just /28) net-mask. Therefore, that part of network can have `2^4 - 2 = 14` hosts and R23 Interface must also have the same net mask. We don't forget that we can have only 62 hosts.<br>
So to give Computer D IP address let's start from the first host in our range. IP address of D will be:
```sh
IP Address:     149.248.202.1       |   10010101.11111000.11001010.00000001
```
And for the second IP (for Router R23 Interface) let's take second host number:
```sh
IP Address:     149.248.202.2       |   10010101.11111000.11001010.00000010
```
After that we can pass Router R23 Interface IP (149.248.202.2) to our `default gateway`, which means that we can reach all IPs which are not in that subnet through that IP by default (`0.0.0.0/0 => 149.248.202.2`).<br><br>
Another subnet is R22 Interface and computers in that network.<br>
In our case that part of the subnet includes just 2 hosts. One for Router R22 Interface and another for client C Interface.<br>
In that part we don't have any known data (not IP addresses not Net-mask). But we must remember that later on for Goal 2 we need to connect to the Internet. So this means that Client C and Router R22 also must have IP addresses in that Network (149.248.202.0/26).<br>
We also need to remember that using IP addresses for Client D's and Router R23 subnet we already used 16 IP addresses (from 149.248.202.0 to 149.248.202.15).<br>
It turns out, that now we have `62 - 16 = 46` free IP addresses, which we can use.<br><br>
Because of the fact that for subnet Router R22 and client C1 Interfaces we need only two IPs, I chose the minimalistic network which will cover those 2 IPs. And the mask is `255.255.255.252` or just `/30`.<br>
```
Notice: Here I choose /30 netmask just for efficiently, you can however use other Masks, such as /29 (255.255.255.248) or /28 (255.255.255.240). That will work too.
```
This mask gives us two hosts.<br>
Now we can calculate two IP addresses, and for calculation I use 149.248.202.17 Network address, because of as mentioned above first 16 (0, 1 to 14 and 15) are used and 149.248.202.17 is first available IP:
```sh
IP Address 1:   149.248.202.17      |   10010101.11111000.11001010.00010001
```
```sh
IP Address 2:   149.248.202.18      |   10010101.11111000.11001010.00010010
```
So Router R22 will have `149.248.202.17` IP address and `255.255.255.252` Net-mask.<br>
And Client C will have `149.248.202.18` IP address and `255.255.255.252` Net-mask.<br>
The final step for ending the goal 1 is to Correct Client C's routing table. 
For that we need to pass router R22 Interface IP address to the Default gateway (that is same as 0.0.0.0/0 or just default). I.e. `0.0.0.0/0 => 149.248.202.17`.
#### Goal 2, Goal 3
For goal 2 and goal 3 we need to connect the computers C and D to the Internet.<br>
In this stage we already configured and connected C and D to the router 2 and now we need to configure the connections between Router 2 and Router 1, Router 1 and the Internet I, and their reverses (Internet I to router 1, and router 1 to router 2).<br><br>
The Internet I is located in Router R12's network, so for router 2 we need to in its routing table write through which interface it can go to that network. So here I wrote `163.25.250.12/28 =>`, but you can write just `0.0.0.0/0 =>` for its default gateway to router 13 Interface (Here that doesn't matter what you will write, both is correct).<br><br>
From second part of that record in routing table we can see that we already have IP address of Router 13 Interface which is `149.248.202.62` and here it also in Network `149.248.202.0/26` range (IPs from one router to another router can be out of Network range, but here we are given in the range).<br>
Using IP addresses for Router 2 R23 and Router 2 R22 subnets we now have `46 - 4 = 42` free and available addresses, which are in this range `149.248.202.21 - 149.248.202.62`.<br>
As we can see above, IP address of router R13 `149.248.202.62` is the last address of range.<br>
For connecting Router 21 to Router 13 we need just two IP addresses from that range, so for them I will use Net-Mask /30 (255.255.255.252) again, to approach addresses sparingly.<br><br>
In this stage it turns out that Router R13 Interface will have `149.248.202.62` IP address and `255.255.255.252` Net-mask, and Router R21 will have `255.255.255.252` Net-mask.<br>
To get the second IP address for that part of the network we just can subtract 1 from the last IP which is 62. So Router R21 IP address will be `149.248.202.61`. (Remember that from our Net-mask (/30) we have one reserved broadcast IP - 149.248.202.63, two free IPs - 62 and 61, and one more reserved for network - 60).
Choosing such network mask in the end we have `42 - 4 = 38` more available hosts. But we don't need them anymore.<br><br>
In this stage our computers already connected to the Internet I but for the reverse connection from the Internet I to our computers we need to configure routing tables for Internet I and Router 1, so they know where to send requests' answers.<br><br>
For that in routing table of the Internet I we need to write through which interface the network `149.248.202.0/26` is located, which is the interface of Router R12: `149.248.202.0/26 => 163.25.250.12`.<br><br>
And for routing table Router 1 we also need to write through which interface the network `149.248.202.0/26` is located, which is the interface of Router 21: `149.248.202.0/26 => 149.248.202.61`. We don't need to look to the second record of the routing table of Router 1, because it just shows us through which interface Router 1's default gateway is located.<br><br>
![NetPractice - level 8](./imgs/level_8.png)
___
### Level 9
___
### Level 10
