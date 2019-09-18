# Scripts-Sprint2

Switch 1

enable
configure terminal
vlan 10
vlan 20
vlan 30
vlan 40
vlan 50
vlan 60
vlan 70
vlan 80
vlan 90
vlan 99
vlan 100
interface f0/1
switchport mode access
switchport access vlan 10
exit
vlan 10 
name RH
interface f0/2
switchport mode access
switchport access vlan 20
exit
vlan 20 
name ADMINISTRAÇÃO
interface f0/3
switchport mode access
switchport access vlan 30
exit
vlan 30 
name QUALIDADE
interface f0/4
switchport mode access
switchport access vlan 40
exit
vlan 40 
name RECEPCAO
interface f0/5
switchport mode access
switchport access vlan 50
exit
vlan 50 
name TI
interface f0/6
switchport mode access
switchport access vlan 60
exit
vlan 60
name ANALISTAS
interface f0/7
switchport mode access
switchport access vlan 70
exit
vlan 70 
name FINANCAS
interface f0/8
switchport mode access
switchport access vlan 80
exit
vlan 80 
name CONSULTORES 
interface f0/9
switchport mode access
switchport access vlan 90
exit
vlan 90 
name VOZ
interface f0/10
switchport mode access
switchport access vlan 100
exit
name Switches/Router/Server
interface g0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,99,100
interface vlan 99
ip address 172.16.0.254 255.255.0.0
ip default-gateway 172.16.0.1
no shutdown
do wr
hostname S1
banner motd "ACESSO APENAS PARA PESSOAS AUTORIZADAS"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
username erick privilege 15 secret SenhaNormal
username ruth privilege 15 secret SenhaNormal
username guilherme privilege 15 secret SenhaNormal
username vinicius privilege 15 secret SenhaNormal
username cleiton privilege 15 secret SenhaNormal
line console 0
password SenhadaConsole
login
exit
service password-encryption
line vty 0 15
password SenhadaVTY
transport input ssh
exec-timeout 10
login local
exit
no shutdown
do wr

Router 1

enable
configure terminal
hostname R1
banner motd "ACESSO APENAS PARA PESSOAS AUTORIZADAS"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
password SenhadaVTY
login
transport input ssh
exec-timeout 10
exit
username erick privilege 15 secret SenhaNormal
username ruth privilege 15 secret SenhaNormal
username guilherme privilege 15 secret SenhaNormal
username cleiton privilege 15 secret SenhaNormal
username vinicius privilege 15 secret SenhaNormal
line console 0
password SenhadaConsole
login
exit
service password-encryption
interface g0/1
interface g0/0.10
encapsulation dot1q 10
ip address 172.16.18.11 255.255.255.128
interface g0/0.20
encapsulation dot1q 20
ip address 172.16.18.129 255.255.255.128
interface g0/0.30 
encapsulation dot1q 30
ip address 172.16.20.65 255.255.255.192
interface g0/0.40
encapsulation dot1q 40
ip address 172.16.20.1 255.255.255.192
interface g0/0.50
encapsulation dot1q 50
ip address 172.16.19.129 255.255.255.128
interface g0/0.60
encapsulation dot1q 60
ip address 172.16.10.1 255.255.254.0
interface g0/0.70
encapsulation dot1q 70
ip address 172.16.19.1 255.255.255.128
interface g0/0.80
encapsulation dot1q 80
ip address 172.16.0.9 255.255.248.0
interface g0/0.90
encapsulation dot1q 90
ip address 172.16.90.1 255.255.248.0
interface g0/0.100
encapsulation dot1q 100
ip address 172.16.20.129 255.255.255.240
interface vlan 99
ip address 172.16.0.1 255.255.255.240
no shutdown
do wr
exit
do wr


Switch 2


enable
configure terminal
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,99,100
interface g0/2 
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,99,100
interface vlan 99
ip address 172.16.0.253 255.255.0.0
no shutdown
ip default-gateway 172.16.0.1
do wr
hostname S2
banner motd "ACESSO APENAS PARA PESSOAS AUTORIZADAS"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
username erick privilege 15 secret SenhaNormal
username ruth privilege 15 secret SenhaNormal
username guilherme privilege 15 secret SenhaNormal
username vinicius privilege 15 secret SenhaNormal
username cleiton privilege 15 secret SenhaNormal
line console 0
password SenhadaConsole
login
exit
service password-encryption
line vty 0 15
password SenhadaVTY
transport input ssh
exec-timeout 10
login local
exit
do wr
