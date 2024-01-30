  
**Le NAT (Network Address Translation)**, est une technique utilisée dans les réseaux informatiques pour permettre à plusieurs dispositifs de partager une seule adresse IP publique pour accéder à Internet. Cela se fait en traduisant les adresses IP privées des dispositifs du réseau local en une seule adresse IP publique.

![[ob_d153ed_nat1.png]]

1. **Sur le routeur Router0**

Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#ip nat inside
Router(config-if)# no shutdown
Router(config)#interface Serial0/3/0
Router(config-if)#ip address 10.10.10.1 255.255.255.0
Router(config-if)#ip nat outside
Router(config-if)# no shutdown

2. **Sur le routeur Router1**

Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 192.168.2.1 255.255.255.0
Router(config-if)#ip nat inside
Router(config-if)# no shutdown
Router(config)#interface Serial0/3/0
Router(config-if)#ip address 10.10.10.2 255.255.255.0
Router(config-if)#ip nat outside
Router(config-if)# no shutdown

2. **Definissons une liste de controle d’acces ([[ACL]])**

**Sur le routeur Router0**

Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
Router(config)# ip nat pool plageA 10.10.10.3 10.10.10.4 netmask 255.255.255.0
Router(config)# ip nat inside source list 1 pool plageA

**Sur le routeur Router1**

Router(config)# ip nat inside source static tcp 192.168.2.100 80 10.10.10.2 80
Router(config)# ip nat inside source static tcp 192.168.2.200 80 10.10.10.2 81