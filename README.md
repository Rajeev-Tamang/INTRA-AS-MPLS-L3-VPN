# INTRA-AS-MPLS-L3-VPN
# R1
> vrf defination nepal-bank
> 
> address-family ipv4
>
> vrf defination laxmi-sunrise-bank
> 
> address-family ipv4
>
> int f 1/0
> 
> vrf forwarding nepal-bank

> ip add 192.168.15.1 255.255.255.0

> no shutdown

> exit
>
> int f 2/0

> vrf forwarding laxmi-sunrise-bank

> ip address 192.168.16.1 255.255.255.0

> no shutdwon

> exit

>

> int f 0/0

> ip address 192.168.12.1 255.255.255.0

> no shutdown

> exit

>

> int loop 0

> ip address 1.1.1.1 255.255.255.255

> exit

> 
