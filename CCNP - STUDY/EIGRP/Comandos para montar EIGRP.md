
![[Pasted image 20241219185818.png]]

## Router 1

enable
configure terminal

! Configuración de interfaces
interface f1/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface f2/0
 ip address 172.16.12.1 255.255.255.252
 no shutdown

interface f3/0
 ip address 172.16.13.1 255.255.255.252
 no shutdown

! Activar EIGRP
router eigrp 100
 network 192.168.1.0 0.0.0.255
 network 172.16.12.0 0.0.0.3
 network 172.16.13.0 0.0.0.3
 no auto-summary

exit
write memory


## Router 2

enable
configure terminal

! Configuración de interfaces
interface f1/0
 ip address 172.16.12.2 255.255.255.252
 no shutdown

interface f2/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown

interface f3/0
 ip address 172.16.23.1 255.255.255.252
 no shutdown

! Activar EIGRP
router eigrp 100
 network 172.16.12.0 0.0.0.3
 network 192.168.2.0 0.0.0.255
 network 172.16.23.0 0.0.0.3
 no auto-summary

exit
write memory

## Router 3

enable
configure terminal

! Configuración de interfaces
interface f1/0
 ip address 172.16.13.2 255.255.255.252
 no shutdown

interface f2/0
 ip address 172.16.23.2 255.255.255.252
 no shutdown

interface f3/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown

! Activar EIGRP
router eigrp 100
 network 172.16.13.0 0.0.0.3
 network 172.16.23.0 0.0.0.3
 network 192.168.3.0 0.0.0.255
 no auto-summary

exit
write memory


