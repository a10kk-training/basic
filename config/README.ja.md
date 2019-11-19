
Networkのサンプルコンフィグです。

```
hostname tax11
!
vlan 10
 untagged ethernet 1
 router-interface ve 10
!
vlan 20
 untagged ethernet 3
 router-interface ve 20
!
interface ethernet 1
 enable
!
interface ethernet 3
 enable
!
interface ve 10
 ip address 10.0.1.11 255.255.255.0
!
interface ve 20
 ip address 10.0.2.11 255.255.255.0
!
ip route 0.0.0.0 /0 10.0.1.1 
!

```

SLB-L4のサンプルコンフィグです。

```
slb server s1 10.0.2.18
   port 80  tcp
!
slb server s2 10.0.2.19
   port 80  tcp
!
slb service-group sg-80 tcp
    method service-least-connection
    member s1 80
    member s2 80
!
slb virtual-server vip1 10.0.1.111
   port 80  tcp
      service-group sg-80
```
