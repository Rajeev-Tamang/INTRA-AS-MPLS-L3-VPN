# INTRA-AS-MPLS-L3-VPN
# R1
> vrf defination nepal-bank
> 
>> address-family ipv4
>
> vrf defination laxmi-sunrise-bank
> 
>> address-family ipv4
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
> 
> no shutdwon
> 
> exit
> 
> int f 0/0
> 
> ip address 192.168.12.1 255.255.255.0
> 
> mpls ip
> 
> no shutdown
> 
> exit
>
> int loop 0
> 
> ip address 1.1.1.1 255.255.255.255
> 
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
>interface loop 0
>
>ip add 3.3.3.3 255.255.255.255
>
>exit
>
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

> ip cef
>
> mpls ip
>
> mpls ldp router-id loopback 0
>
> int f 0/0
>
> mpls ip
>
> ip address 192.168.34.4 255.255.255.0
>
> no shut
>
> exit
>
> vrf defination nepal-bank
>
> address-family ipv4
>
> vrf defination laxmi-sunrise-bank
>
> address-family ipv4
>
> interface f 1/0
>
> vrf forwarding nepal-bank
>
> ip address 192.168.47.4 255.255.255.0
>
> no shut
>
> exit
>
> interface f 2/0
>
> vrf forwarding laxmi-sunrise-bank
>
> ip address 192.168.48.4 255.255.255.0
>
> no shut
>
> exit
>
> int loop 0
>
> ip address 4.4.4.4 255.255.255.255
>
> no shut
>
> exit


# R5
>
>int f 1/0
>
>no shut
>
>ip add 192.168.15.5 255.255.255.0
>
>exit
>
>int loop 0
>
>ip add 10.10.10.10 255.255.255.255
>
>int loop 1
>
>ip add 11.11.11.11 255.255.255.255
>
>int loop 2
>
>ip add 12.12.12.12 255.255.255.255
>
>exit
>
>router ospf 1
>
>network 10.10.10.10 0.0.0.0 area 0
>
>network 11.11.11.11 0.0.0.0 area 0
>
>network 12.12.12.12 0.0.0.0 area 0
>
>exit


# R6
>
>>int f 2/0
>
>no shut
>
>ip add 192.168.16.6 255.255.255.0
>
>exit
>
>int loop 0
>
>ip add 10.10.10.10 255.255.255.255
>
>int loop 1
>
>ip add 11.11.11.11 255.255.255.255
>
>int loop 2
>
>ip add 12.12.12.12 255.255.255.255
>
>exit
>
>router rip
>
>no auto
>
>version 2
>
>network 10.0.0.0
>
>network 11.0.0.0
>
>network 12.0.0.0 
>
>exit

# R7

>
>>int f 1/0
>
>no shut
>
>ip add 192.168.47.7 255.255.255.0
>
>exit
>
>int loop 0
>
>ip add 20.20.20.20 255.255.255.255
>
>int loop 1
>
>ip add 30.30.30.30 255.255.255.255
>
>int loop 2
>
>ip add 40.40.40.40 255.255.255.255
>
>exit
>
>router ospf 1
>
>network 20.20.20.20 0.0.0.0 area 0
>
>network 30.30.30.30 0.0.0.0 area 0
>
>network 40.40.40.40 0.0.0.0 area 0
>
>exit


# R8

>int f 2/0
>
>no shut
>
>ip add 192.168.48.8 255.255.255.0
>
>exit
>
>
>int loop 0
>
>ip add 20.20.20.20 255.255.255.255
>
>int loop 1
>
>ip add 30.30.30.30 255.255.255.255
>
>int loop 2
>
>ip add 40.40.40.40 255.255.255.255
>
>exit
>
>router rip
>
>no auto
>
>version 2
>
>network 20.0.0.0
>
>network 30.0.0.0
>
>network 40.0.0.0 
>
>exit
>
