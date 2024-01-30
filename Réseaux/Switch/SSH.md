
Le SSH va permettre de se connecter a distance sur le port 22 au switch 

conf# hostname <nom_hôte> `modifier le nom du switch`
conf# ip domain-name <nom_domaine> `donner un nom de domaine` 
conf# enable password <mot_de_passe> `Ajouter un mdp au passage en mode enable`
conf# crypto key generate rsa `Génère une clés de chiffrement` 
How many bits in the modulus [512]: `1024 mettre une cles en 1024 c'est plus sécuriser` 

(config)# ip ssh version 2  
(config)#line vty 0 4 
(config-line)#transport input ssh `n’accepter que les connexions SSH au routeur ou au switch`
(config-line)#transport output ssh `ne permettre que des connexions SSH vers d’autres équipements`
(config-line)#login local` enregistrer le compte utilisateur existant comme compte permettant de mettre en place la connexion en entrant`
(config-line)#exit

Si de compte utilisateur n'existe pas retourner en mode config 

username <nom_utilisateur> password <mot_de_passe>

ne pas oublier d'enregistrer avec la commande suivante:

copy running-config startup-config