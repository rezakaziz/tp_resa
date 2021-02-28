# Implémentation d’une plateforme VPN/MPLS

La société CSIQ est constitué de 6 sites distants. Elle a besoin d’une connectivité vers ses sites
distants en gardant son réseau confidentiel.
Le 6 sites sont répartis comme suit : le site central, 3 magasins et 2 usines. Ci-dessous
l’architecture générale du réseau de l’entreprise :

Pour relier les 6 sites, la société sollicite un réseau d’opérateur qui possède un backbone IP
routé en MPLS.
Les sites sont connectés au réseaux MPLS via des routeurs CE (Customer Edge). On dispose
de 6 sites ce qui nécessite à 6 routeurs CE.
L’opérateur fournit alors des routeurs PE (Provider Edge) a chaque site qui va permettre une
connectivité au réseau IPv4. Il y a au total 4 routeur PE. Pour transmettre les paquets on passe
d’un PE à un autre PE par les routeurs du backbone opérateur P (Provider), qui ne connaissent
pas les routes privées de la société CSIQ.
Pour pouvoir communiquer entre eux, les PE ont besoin de connaître les routes privées IPv4
des CE. Ces dernières apprises par le PE vont être transmises aux autres routeurs PE du VPN
grâce à BGP et son extension multi protocole VPN-IPv4 (MP-BGP).
La société CSIQ souhaite créer des VPN entre ces différents sites pour rendre l’accès aux
données de l’entreprise plus confidentiel et permanent.


Travail demandé :
1. Proposer un plan d’adressage pour les différents sites et pour le réseau du provider. Les
réseaux connectés aux CE sont de préfixe /24 alors que les réseaux point à point sont de
préfixe /30.
Le 3ème octet des adresses IP doit être le numéro de votre équipe
Pour les réseaux locaux, vous pouvez utiliser les interfaces de loopback.
2. Configurer les protocoles de routage dynamiques :
a. Les réseaux CE1-PE1, CE2-PE2 et CE3-PE3 exécutent le protocole RIP alors que les
réseaux CE4-PE3, CE5-PE4 et CE6-PE4 exécute le protocole EIGRP.
b. A l’intérieur du réseau du provider, les routeurs PE et P exécutent le protocole OSPF.
3. Les paquets à l’intérieur du réseau du provider sont acheminés à la l’aide de la commutation
MPLS.
4. Concevoir l’architecture détaillée du réseau avec les VPN/MPLS en détaillant les
principaux choix des éléments de base de la configuration.
a) La société CSIQ souhaite créer 3 VPN point-à-point entre les 3 magasins et le Head
Quarter. Cela signifie que les utilisateurs au niveau d’un magasin doivent
obligatoirement passer par le HQ pour atteindre le réseau d’un autre magasin. On parle
donc, d’une architecture VPN Hub & Spoke.
b) Les 2 usines et le HQ forment un VPN maillé où les utilisateurs d’un réseau peuvent
atteindre un autre réseau directement via le réseau du provider. L’architecture VPN en
question est de type Full Mesh.
