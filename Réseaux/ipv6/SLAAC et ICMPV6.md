
![[Pasted image 20240129141115.png]]


Les + pour ICMPV6 sont:

-Beaucoup plus robuste que l'icmp v4
-contient de nouvelles fonctionnalités et des améliorations 


Il permet d'indiquer a tous les appareils IPV6 sur le lien pour leur dire comment ils recevront les informations d'adresse ipv6

![[Pasted image 20240129142358.png]]

# **Les messages RA**

La commande` ipv6 unicast-routing` permet 

- **Transmettre les paquets IPV6**
- **Active le routage statique et dynamique ipv6**
- **Envoi les annonces Router Avertissements ICMPv6**

Il y a différente option:
![[Pasted image 20240129144049.png]]

==Par défaut :== **Les deux drapeaux sont mis à 0** (option 1)
•Utilisez moi (RA) pour toutes vos informations d'adressage, aucune information supplémentaire n'est disponible via DHCPv6.

==Other Configuration Flag== **quand il est défini à «1»** (Option 2)
•Utilisez-moi (RA) pour votre adresse mais vous devez obtenir d'AUTRES informations d'un serveur DHCPv6 sans état.

==Managed Configuration Flag== **quand il est défini à «1»** (Option 3)
•Le client doit obtenir TOUTES ses informations de GESTION à partir d'un serveur DHCPv6 avec état, sauf la passerelle par défaut.