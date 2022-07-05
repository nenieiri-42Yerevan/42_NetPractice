# NetPractice
## Solutions
### Level 1
For two or more computers to communicate, they need to be in the same network (i.e. their network addresses need to be the same). Otherwise, if their network addresses differ, a router will be needed.
#### Goal 1
Here, for Goal 1 there isn't a router and the computers are connected to each other directly.
In addition, we know the ip address and network mask of client B so we can easily calculate its network address, which will be equal to __104.95.23.0__:
```sh
IP Address:     104.95.23.12        |   01101000.01011111.00010111.00001100
Net-mask:       255.255.255.0 = 24  |   11111111.11111111.11111111.00000000
                                        & (Bitwise and)
Network:        104.95.23.0/24      |   01101000.01011111.00010111.00000000
```
This means that client A must also have the same network address: __104.95.23.0__. 
In this exercise we are already given the network mask of client A __255.255.255.0__.
This network mask shows that in this network we can have `2^8 - 2 = 254` hosts (computers).
Where the smallest one will have the following address:
```
HostMin:        0.0.0.1             |   00000000.00000000.00000000.00000001
```
and the biggest:
```sh
HostMax:        0.0.0.254           |   00000000.00000000.00000000.11111110
```
The client B's host number is 0.0.0.12, so we can choose any host from the hosts' rang except for 12. For example, if I choose 13 then client A's host will be:
```sh
A Client Host Number: 0.0.0.13      |   00000000.00000000.00000000.00001101
```
By combining network address with host number, we will get the ip address of client A, which will be
```sh
Network:        104.95.23.0/24      |   01101000.01011111.00010111.00000000
Host Number:    0.0.0.13            |   00000000.00000000.00000000.00001101
                                        | (Bitwise or)
IP Address:     104.95.23.13        |   01101000.01011111.00010111.00001101
```
So __104.95.23.13__ is one of the correct answers.
Summing up, we can say that correct answers' range is __(104.95.23.1 - 104.95.23.254)__, except for 104.95.23.12.
#### Goal 2
This is the same as for Goal 1.
From Client C we get Network address which is __211.191.0.0__:
```sh
IP Address:     211.191.185.75      |   11010011.10111111.10111001.01001011
Net-mask:       255.255.0.0 = 16    |   11111111.11111111.00000000.00000000
                                        & (Bitwise and)
Network:        211.191.0.0/16      |   11010011.10111111.00000000.00000000
```
Client D has 255.255.0.0 Network Mask which means that this network can has `2^16 - 2 = 65,534` hosts.
Where the smallest one will have the following address:
```
HostMin:        0.0.0.1             |   00000000.00000000.00000000.00000001
```
and the biggest:
```sh
HostMax:        0.0.255.254         |   00000000.00000000.11111111.11111110
```
The client C’s host number is 0.0.185.75, so we can choose any host from the hosts’ rang except for that. For example, if I choose 185.78 then client D’s host will be:
```sh
A Client Host Number: 0.0.185.78    |   00000000.00000000.10111001.01001110
```
By combining network address with host number, we will get the ip address of client A, which will be
```sh
Network:        211.191.0.0/16      |   11010011.10111111.00000000.00000000
Host Number:    0.0.185.254         |   00000000.00000000.10111001.01001110
                                        | (Bitwise or)
IP Address:     211.191.185.254     |   11010011.10111111.10111001.01001110
```
So __211.191.185.254__ is one of the correct answers.
Summing up, we can say that correct answers' range is __(211.191.0.1 - 211.191.255.254)__, except for 211.191.185.75.

![NetPractice - level 1](./level1.png)
