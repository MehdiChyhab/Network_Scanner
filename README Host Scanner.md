 Host Scanner Python
 Ce projet est un scanner réseau en Python qui permet de détecter les hôtes actifs dans un sous-réseau en utilisant des paquets UDP et l'écoute de réponses ICMP.

 Description:
 
Le scanner fonctionne en envoyant un message UDP personnalisé à chaque hôte d'un sous-réseau défini.
Si l'hôte est actif mais que le port est fermé, il renvoie une réponse ICMP de type 3, code 3 (Port Unreachable), ce qui permet de l'identifier comme "up".

Fonctionnement :
1-Envoi de paquets UDP via un thread séparé.
2-Capture des paquets ICMP entrants via un socket RAW.
3-Filtrage des réponses pertinentes et extraction de l'adresse IP source.
4-Affichage des hôtes actifs détectés.

Structure du projet:
SUBNET : le sous-réseau à scanner (par défaut : 192.168.1.0/24)
MESSAGE : message unique envoyé via UDP pour identifier la réponse.
IP : classe de parsing de l'en-tête IP.
ICMP : classe de parsing de l'en-tête ICMP.
udp_sender() : envoie un paquet à chaque IP du sous-réseau.
Scanner : classe principale pour la capture et l'analyse des paquets.

Résultat attendue:
PS C:\Users\Administrator\Desktop\Network_Scanner> python host_scanner.py 192.168.1.3
hitting promiscuous mode...
Host up: 192.168.1.3
