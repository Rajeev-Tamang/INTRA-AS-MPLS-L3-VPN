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
> 
> ip add 192.168.15.1 255.255.255.0
> 
> no shutdown
> 
> exit
>
> int f 2/0
> 
> vrf forwarding laxmi-sunrise-bank
> 
> ip address 192.168.16.1 255.255.255.0

> no shutdwon

> exit

>

> int f 0/0

> ip address 192.168.12.1 255.255.255.0
> 
> mpls ip
> 
> no shutdown

> exit

>

> int loop 0

> ip address 1.1.1.1 255.255.255.255

> exit
>
> ip cef
> 
> mpls ip
>
> mpls ldp router-id loopback 0
>


# R2
>
>ip cef
>
>mpls ip
>
>mpls ldp router-id loopback 0
>
>
>int f 0/0
>
>ip address 192.168.12.2 255.255.255.0
>
>mpls ip
>
>no shut
>
>int f 1/0
>
>ip address 192.168.23.2 255.255.255.0
>
>mpls ip
>
>no shut
>
>exit
>
>int loop 0
>
>ip address 2.2.2.2 255.255.255.2555
>
>exit
>
>router ospf 1
>
>network 192.168.12.0 0.0.0.255 area 0
>
>network 192.168.23.0 0.0.0.255 area 0
>
>network 2.2.2.2 0.0.0.0 area 0
>
>exit

# R3

>ip cef
>
>mpls ip
>
>mpls ldp router-id loopback 0
>
>int f 1/0
>
>mpls ip
>
>ip address 192.168.23.3 255.255.255.0
>
>no shut
>
>exit
>
>int f 0/0
>
>mpls ip
>
>ip address 192.168.34.3 255.255.255.0
>
>no shut
>
>exit
>
>router ospf 1
>
>network 192.168.23.0 0.0.0.255 area 0
>
>network 192.168.34.0 0.0.0.255 area 0
>
>network 3.3.3.3 0.0.0.0 area 0
>
>exit

# R4

