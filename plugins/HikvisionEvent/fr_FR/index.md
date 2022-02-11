---
layout: default
lang: fr_FR
title: Plugin Hikvision Event
description: Documentation du plugin Hikvision Event
---

Ce plugin permet de récupérer les alarmes et exécuter quelques actions sur vos équipements Hikvision (et sous-marques).
Pour la beta, le plugin ne gère que la remontée d'alarme. Les commandes actions arriveront dans de futures versions.
Sont supportés à date :
- La plupart des **caméras** Hikvision (si certaines ne fonctionnent pas, écrivez moi sur la community)
- La plupart des **NVR** (non testés)
- Les **portiers doorbell** ne sont pour l'instant pas supportés (des tests sont en cours)


Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Il n'y a aucune configuration particulière à faire.
Il est nécessaire de ne pas toucher aux paramètres du démon. Seul le port peut être modifié sur le port par défaut est déjà utilisé sur votre machine jeedom
Quelques options sont configurables :
- **Port du démon** qui sert à la communication entre le plugin et le démon (Il est recommandé de ne pas le modifier)
- **Durée de rétention des images** pour la durée ou le plugin conserve les images enregistrées dans le répertoire data du plugin.
- **Pièce par défaut**
- **Ignorer le heartbeat** (evenement videoloss inactive de hikvision)

Il sera possible dans une version ultérieure de détecter les périphériques Hikvision sur votre réseau local.

Il est également possible de réparer NodeJS le cas échéant.

Configuration des équipements 
=============================

La configuration des équipements Hikvision est accessible à partir du menu
plugins puis Sécurité. Vous retrouvez ici :

-   un bouton pour créer un équipement manuellement
-   un bouton pour afficher la configuration du plugin
-   un bouton qui vous donne une vue d'ensemble de tous vos équipements à un moment donné (Fonction à venir)
-   enfin en dessous vous retrouvez la liste de vos équipements Hikvision

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

-   **Onglet Equipement** :
-   **Nom de l’équipement** : nom de votre équipement
-   **Activer** : permet de rendre votre équipement actif
-   **Visible** : le rend visible sur le dashboard
-   **Objet parent** : indique l’objet parent auquel appartient l’équipement
-   **Protocole** : Protocole (HTTPS recommandé) à utiliser pour la connexion à équipement Hikvision.
-   **IP** : l'IP de l'équipement Hikvision (doit être fixe sur votre réseau local)
-   **Port** : Le port de l'équipement Hikvision (Généralement 80 pour HTTP et 443 pour HTTPS).

> Si vous avez modifié le port par défaut (80 ou 443) vous pouvez le modifier

-   **Utilisateur** : Utilisateur de l'équipement Hikvision (Un utilisateur spécifique à l'API ISAPI est nécessaire avec les droits suffisants).
-	**Mot de passe** : Mot de passe de l'équipement Hikvision.

> NB : Lors de l'enregistrement de l'équipement. Si une connexion en cours est déjà effective sur l'équipement, la connexion est **tuée** puis **relancé**.

**Commandes Equipement Hikvision**
================================
Les commandes d'alarmes sont automatiquement créées au fil de leur arrivée.
A moins de savoir précisément ce que vous souhaitez utiliser comme alarme et si vous souhaitez dans un premier temps toutes les obtenir, il est conseillé de toutes les activer sur votre équipement Hikvision. Cela créera les commandes, faites votre marché, puis désactiver sur la caméra celles que vous ne souhaitez pas utiliser.

Autant de commandes info sont créées que de 
- **Canaux** : 1 pour les caméras, plusieurs pour les NVR
- **Type d'alarme** : fielddetection, linedetection, regionEntrance, unattendedBaggage, audioexception, facedetection, attendedBaggage, diskError, faceCapture, scenechangedetection, VMD, ...
- **Region** : Générallement 4 possibles pour la plupart des évènements intelligents  
- **Target** : La cible détectée human ou vehicule

Par exemple, cette commande info binaire est créée : **Chan 1 regionEntrance Region 1 human**
Libre à vous de la renommer le cas échéant.

> NB : Les évènements intelligentes sont plus robustes et plus fiables que les évènements simple. Par exemple la détection intrusion intelligente (fielddetection) par rapport à la détection de mouvement simple (VMD).

Il est nécessaire d'activer chaque évènement désiré et d'activer pour chaque la fonction **Avertir le centre de surveillance** tel indiqué sur la capture ci-dessous.
![event](https://user-images.githubusercontent.com/60837526/153619174-5be660ec-9def-426d-9249-ff0ba6389d57.jpg)

**Paramètrage des caméras ou caméras ou NVR Hikvision **
================================

Protection Globale
-----------------------
- **Statut protection** : Binaire indiquant l'état de la protection globale
- **Activer la protection** : Action permettant d'activer la protection globale
- **Désactiver la protection** : Action permettant de désactiver la protection globale

**Correspondance AdGuard** :




Filtrage Global
-----------------------
- **Statut Filtrage Global** : Binaire indiquant l'état du filtrage global
- **Activer le Filtrage Global** : Action permettant d'activer le filtrage global
- **Désactiver le Filtrage Global** : Action permettant de désactiver le filtrage global

**Correspondance AdGuard** (Paramètres > Paramètres généraux > Bloquer les domaines à l'aide des filtres et fichiers hosts) :

![image](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Sécurité de navigation Globale
-----------------------
- **Statut Sécurité de navigation Globale** : Binaire indiquant l'état de la Sécurité de navigation Globale
- **Activer la Sécurité de navigation Globale** : Action permettant d'activer la Sécurité de navigation Globale
- **Désactiver la Sécurité de navigation Globale** : Action permettant de désactiver la Sécurité de navigation Globale

**Correspondance AdGuard** (Paramètres > Paramètres généraux > Utiliser le service Sécurité de navigation d'AdGuard) :

![image](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)


**Paramètrage des portiers doorbell Hikvision **
================================
A venir suivant compatibilité.
authentification DIGEST obligatoire sur certains modèles.
flux alertStream vide et non bloquant


