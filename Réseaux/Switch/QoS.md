

![[Pasted image 20240130132150.png]]


![[Pasted image 20240130132504.png]]

![[Pasted image 20240130132519.png]]



## Étape 1 déclaration de la classe de 
```
MonRouteur#configure terminal 
MonRouteur(config)#class-map match-all prio-sur-interface
MonRouteur(config-cmap)#match input-interface g0/0
MonRouteur(config-cmap)#exit MonRouteur(config)#
```

Pour vérifier la déclaration de la classe il suffit de faire:

```
#•show class-ma
```

## Étape 2 : déclaration d'une politique de QoS


`MonRouteur (config)#policy-map ma-politique-qos` 
`MonRouteur (config-pmap)#class prio-sur-interface`
`MonRouteur (config-pmap-c)#set ip dscp cs7` # ==cs7 permet de mettre priorité 7 se qui donne le maximum en débit== 
`MonRouteur (config-pmap-c)#exit MonRouteur
`(config-pmap)#exit` 
`MonRouteur (config)#`
![[Pasted image 20240130141042.png]]
## Étape 3 : application de la politique de QoS sur une interface

```
MonRouteur(config)#interface g0/2 
MonRouteur(config-if)#service-policy output ma-politique-qos 
MonRouteur(config-if)#exit
MonRouteur(config)#exit
```


## Exemple 2 : priorité basse pour le protocole FTP

### Étape 1 : déclaration de la classe de flux

```
MonRouteur (config)#class-map match-all prio-sur-ftp 
MonRouteur (config-cmap)#match protocol ftp 
MonRouteur (config-cmap)#exit 
MonRouteur (config)#
```

### Étape 2 : déclaration d’une politique QoS

```
MonRouteur (config)#policy-map ma-politique-qos
MonRouteur (config-pmap)#class prio-sur-ftp 
MonRouteur (config-pmap-c)#set ip dscp cs1
MonRouteur (config-pmap-c)#exit MonRouteur (config-pmap)#exit 
MonRouteur (config)#
```
### Seconde possibilité

```
MonRouteur(config)#policy-map autre-politique 
MonRouteur(config-pmap)#class prio-sur-ftp 
MonRouteur(config-pmap-c)#bandwidth percent 10
```

nous avons réservé 10 % de la bande passante au trafic FT