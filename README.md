# Implémentation d’une plateforme VPN/MPLS

## Description
Ce projet vise à implémenter une solution VPN/MPLS pour la société CSIQ, qui possède **6 sites distants** : un siège central (HQ), **3 magasins** et **2 usines**. L’objectif est d’assurer une connectivité sécurisée entre les sites via un réseau MPLS avec deux types d’architectures VPN :
- **Hub & Spoke** : pour la communication entre les magasins via le siège.
- **Full Mesh** : pour une communication directe entre les usines et le HQ.

Le backbone du réseau est basé sur **BGP** (MP-BGP), **OSPF**, **RIP**, **EIGRP** et MPLS pour la commutation des paquets.

## Topologie du Réseau
La topologie est constituée de :
- **6 Routeurs CE** (Customer Edge)
- **4 Routeurs PE** (Provider Edge)
- **4 Routeurs P** (Provider) pour le backbone MPLS

Le réseau est configuré de sorte que :
- Les CE1-PE1, CE2-PE2 et CE3-PE3 utilisent **RIP**.
- Les CE4-PE3, CE5-PE4 et CE6-PE4 utilisent **EIGRP**.
- Les PE et P dans le réseau provider utilisent **OSPF** pour la connectivité.

Les sites de CSIQ sont reliés au réseau MPLS et échangent leurs routes via **MP-BGP**.

## Plan d’Adressage
### Réseau de l'entreprise (CSIQ)
- **HQ** : `10.0.15.0/24`
- **Magasin 1** : `10.1.15.0/24`
- **Usine 1** : `10.2.15.0/24`
- **Usine 2** : `10.3.15.0/24`
- **Magasin 3** : `10.4.15.0/24`
- **Magasin 2** : `10.5.15.0/24`

### Réseau Provider
- **Réseaux point-à-point** : Préfixes `/30` entre les CE et PE
- **Loopback** : Utilisation d'adresses `/32` pour MP-BGP

## Tests de Connectivité
Les tests effectués ont permis de valider :
- **Connectivité directe** entre les usines et HQ.
- **Connectivité Hub & Spoke** entre magasins via HQ.
- **Absence de communication** entre les magasins et les usines.

### Résultats
- **Ping** et **Traceroute** ont été utilisés pour vérifier les chemins de communication.
- Résultats positifs selon les exigences.

## Membres de l'Équipe
- **MEDJADJI Chaima**
- **AMIEUR Nardjes**
- **AZIZ Rezak**
- **MECHARBAT Lotfi Abdelkrim**


### Superviseur
- **Hamani Nacer**
