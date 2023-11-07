# Configuration service DHCP routeur cisco 1841

Il faut d’abord s’assurer que le routeur est vide :
```
router> enable 
router# erase startup-config
```

ensuite on configure le VLAN : 

```
router> en (= enable)
router# conf t (= config terminal)
router(config)# int vlan1 (= interface vlan1)
router(config-if)# ip address 192.168.1.1 255.255.255.0
router(config-if)# ip nat source inside
router(config-if)# no shutdown
router(config-if)# exit
router(config)#
```

Configuration DHCP : 

```
router(config)# ip dhcp pool NomDuDHCP
router(config-if)# network 192.168.1.0 255.255.255.0
router(config-if)# default-router @IP du port FA0 ou FA1
router(config-if)# dns-server 1.1.1.1
router(config-if)# exit
router(config)#
```

enlever une plage d’ip

```
router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.20
```