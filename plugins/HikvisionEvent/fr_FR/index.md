---
layout: default
lang: fr_FR
title: Plugin AdGuard Home
description: Documentation du plugin AdGuard Home
---

Ce plugin permet de monitorer et exécuter quelques actions sur vos AdGuard Home.

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Il n'y a aucune configuration particulière à faire

Configuration des équipements 
=============================

La configuration des équipements AdGuard est accessible à partir du menu
plugins puis Monitoring. Vous retrouvez ici :

-   un bouton pour créer un équipement manuellement

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements à un moment donné

-   enfin en dessous vous retrouvez la liste de vos équipements AdGuard Home et des clients liés

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

-   **Onglet Equipement** :

-   **Nom de l’équipement** : nom de votre équipement

-   **Activer** : permet de rendre votre équipement actif

-   **Visible** : le rend visible sur le dashboard

-   **Objet parent** : indique l’objet parent auquel appartient l’équipement

**Pour AdGuard uniquement**

-   **Ip du serveur** : l'ip du serveur AdGuard Home.

> Si vous avez modifié le port par défaut (80) vous pouvez ajouter votre port ici sous la forme ip:port

-   **Utilisateur** : Utilisateur AdGuard Home.

-	**Mot de passe** : Mot de passe de l'utilisateur AdGuard Home.

-	**Auto-Actualisation (cron)** : delais pour vérifier les données sur AdGuard Home, 5min par défaut.

Une fois AdGuard Home ajouté et sauvegarde de l'équipement, les clients trouvés dans AdGuard Home sont ajoutés en tant qu'équipements séparés.

Si vous **ajoutez un client** par la suite, il sera ajouté **automatiquement de la nuit**, pour forcer son ajout dans jeedom, **re-sauvegardez l'équipement AdGuard Home**.

Si vous **retirez un client** par la suite, il sera désactivé **automatiquement de la nuit**, pour forcer sa désactivation dans jeedom, **re-sauvegardez l'équipement AdGuard Home**.

> NB : Un équipement de type **Client**, doit être **désactivé pour être supprimable**.

**Commandes Equipement AdGuard**
================================
- **Rafraichir** : Permet de rafraichir manuellement l'équipement en plus de l'auto-actualisation
- **Online** : Binaire indiquant si AdGuard répond correctement aux demandes
- **Update AdGuard Dispo** : Binaire indiquant si une mise à jour est disponnible
- **Update AdGuard** : Action permettant de mettre à jour AdGuard (si une mise à jour est disponible)

Protection Globale
-----------------------
- **Statut protection** : Binaire indiquant l'état de la protection globale
- **Activer la protection** : Action permettant d'activer la protection globale
- **Désactiver la protection** : Action permettant de désactiver la protection globale

**Correspondance AdGuard** :

![image](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

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

Contrôle Parental Global
-----------------------
- **Statut Contrôle Parental Global** : Binaire indiquant l'état du Contrôle Parental Global
- **Activer le Contrôle Parental Global** : Action permettant d'activer le Contrôle Parental Global
- **Désactiver le Contrôle Parental Global** : Action permettant de désactiver le Contrôle Parental Global

**Correspondance AdGuard** (Paramètres > Paramètres généraux > Utiliser le contrôle parental d'AdGuard) :

![image](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Recherche Sécurisée Globale
-----------------------
- **Statut Recherche Sécurisée Globale** : Binaire indiquant l'état de la Recherche Sécurisée Globale
- **Activer la Recherche Sécurisée Globale** : Action permettant d'activer la Recherche Sécurisée Globale
- **Désactiver la Recherche Sécurisée Globale** : Action permettant de désactiver la Recherche Sécurisée Globale

**Correspondance AdGuard** (Paramètres > Paramètres généraux > Renforcer la recherche sécurisée) :

![image](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Services Globaux
-----------------------
- **Services Bloqués** : Chaine indiquant les services bloqués globalement
- **Bloquer un service** : Action permettant de bloquer un service de la liste
- **Débloquer un service** : Action permettant de débloquer un service de la liste
- **Bloquer tous les services** : Action permettant de bloquer tous les services de la liste
- **Débloquer tous les services** : Action permettant de débloquer tous les services de la liste

**Correspondance AdGuard** (Filtres > Services bloqués) : 

![image](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet Bloqué via DNS
-----------------------
- **Statut Internet Bloqué via DNS** : Binaire indiquant si on a bloqué internet via le DNS
- **Bloquer tout internet via DNS** : Action permettant de bloquer internet via le DNS
- **Débloquer tout internet via DNS** : Action permettant de débloquer internet via le DNS

**Correspondance AdGuard** (Filtres > Règles de filtrage personnalisées > ajout de la règle : `||*^$important` en premier) : 

![image](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Règle filtrage personnalisée
-----------------------
- **Ajouter une règle filtrage personnalisée** : Champ permettant d'ajouter une règle de filtrage personnalisée en premier (orthographe parfaite, sans guillemets autour)
- **Retirer une règle filtrage personnalisée** : Champ permettant de retirer une règle de filtrage personnalisée (orthographe parfaite, sans guillemets autour)

Voir [ici](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**Correspondance AdGuard** (Filtres > Règles de filtrage personnalisées > ajout de la règle donnée en premier)

Statistiques
-----------------------
- **Réinitialiser Statistiques** : Permet de remettre à zéro les statistiques
- **Requêtes DNS** : indique le nombre de requêtes DNS traitées au cours des 24 dernières heures
- **Bloqués par Filtres** : indique le nombre de requêtes DNS bloquées par les filtres adblock et les listes de blocage des hôtes
- **Tentatives de malware-hameçonnage bloquées** : indique le nombre de requêtes DNS bloquées par le module Sécurité de navigation d'AdGuard
- **Recherches sécurisées forcées** : indique le nombre de requêtes DNS faites avec la Recherche securisée
- **Sites à contenu adulte bloqués** : indique le nombre de sites à contenu adulte bloqués
- **Temps moyen de traitement** : indique le temps moyen (en millisecondes) de traitement d'une requête DNS

**Correspondance AdGuard** (Paramètres > Paramètres généraux > Configuration des statistiques > bouton Effacer les statistiques) :

![image](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**et** (Tableau de bord > Statistiques générales) :

![image](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Commandes Equipement Client**
================================

Utiliser les Paramètres Généraux
--------------------------------
- **Statut Utiliser les Paramètres Généraux** : Binaire indiquant si on a activé Utiliser les Paramètres Généraux
- **Activer Utiliser les Paramètres Généraux** : Action permettant d'activer Utiliser les Paramètres Généraux
- **Désactiver Utiliser les Paramètres Généraux** : Action permettant de désactiver Utiliser les Paramètres Généraux

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Paramètres > Utiliser les paramètres généraux (1)) :

![image](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filtrage
--------------------------------
- **Statut Filtrage** : Binaire indiquant l'état du filtrage
- **Activer le Filtrage** : Action permettant d'activer le filtrage
- **Désactiver le Filtrage** : Action permettant de désactiver le filtrage

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Paramètres > Bloquer les domaines à l'aide des filtres et fichiers hosts (2))

Sécurité de navigation
-----------------------
- **Statut Sécurité de navigation** : Binaire indiquant l'état de la Sécurité de navigation
- **Activer la Sécurité de navigation** : Action permettant d'activer la Sécurité de navigation
- **Désactiver la Sécurité de navigation** : Action permettant de désactiver la Sécurité de navigation

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Paramètres > Utiliser le service Sécurité de navigation d'AdGuard (3))

Contrôle Parental
-----------------------
- **Statut Contrôle Parental** : Binaire indiquant l'état de le Contrôle Parental
- **Activer le Contrôle Parental** : Action permettant d'activer le Contrôle Parental
- **Désactiver le Contrôle Parental** : Action permettant de désactiver le Contrôle Parental

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Paramètres > Utiliser le contrôle parental d'AdGuard (4))

Recherche Sécurisée
-----------------------
- **Statut Recherche Sécurisée** : Binaire indiquant l'état de la Recherche Sécurisée
- **Activer la Recherche Sécurisée** : Action permettant d'activer la Recherche Sécurisée
- **Désactiver la Recherche Sécurisée** : Action permettant de désactiver la Recherche Sécurisée

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Paramètres > Renforcer la recherche sécurisée (5))

Utiliser les services bloqués globlaux
--------------------------------
- **Statut Utiliser les services bloqués globlaux** : Binaire indiquant si on a activé Utiliser les services bloqués globlaux
- **Activer Utiliser les services bloqués globlaux** : Action permettant d'activer Utiliser les services bloqués globlaux
- **Désactiver Utiliser les services bloqués globlaux** : Action permettant de désactiver Utiliser les services bloqués globlaux

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Bloquer des services spécifiques > Utiliser les services bloqués globaux (1)):

![image](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Services spécifiques
-----------------------
- **Services Bloqués** : Chaine indiquant les services bloqués spécifiquement pour ce client
- **Bloquer un service** : Action permettant de bloquer un service de la liste spécifiquement pour ce client
- **Débloquer un service** : Action permettant de débloquer un service de la liste spécifiquement pour ce client

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Bloquer des services spécifiques > les services (2))

- **Bloquer tous les services** : Action permettant de bloquer tous les services de la liste spécifiquement pour ce client
- **Débloquer tous les services** : Action permettant de débloquer tous les services de la liste spécifiquement pour ce client

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Bloquer des services spécifiques > Tout bloquer/Tout débloquer (3))

Internet Bloqué via DNS
-----------------------
- **Statut Internet Bloqué via DNS** : Binaire indiquant si on a bloqué internet via le DNS pour ce client
- **Bloquer tout internet via DNS** : Action permettant de bloquer internet via le DNS pour ce client
- **Débloquer tout internet via DNS** : Action permettant de débloquer internet via le DNS pour ce client

**Correspondance AdGuard** (Filtres > Règles de filtrage personnalisées > ajout de la règle : `||*^$client='NomClient',important` en premier)

![image](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Identifiants
-----------------------
- **Identifiant(s)** : Chaine contenant les identifiants actuels du client
- **Ajouter un identifiant** : Action permettant d'ajouter un identifiant au client (sans guillemets autour !!)
- **Retirer un identifiant** : Action permettant de retirer un identifiant au client (sans guillemets autour !!)

> **Attention, s'il existe sur un autre client, il faut d'abord le retirer de ce client ! AdGuard n'autorise pas deux clients a partager les mêmes identifiants (logique ;))**

**Correspondance AdGuard** (Paramètres > Paramètres du client > Modifier Client > Identifiant) :

![image](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
