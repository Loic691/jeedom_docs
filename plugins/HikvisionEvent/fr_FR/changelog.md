---
layout: default
lang: fr_FR
title: Plugin Hikvision Event Home - Changelog
description: Changelog du plugin Hikvision Event
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour pour la compatibilité Jeedom V4
> Attention, Suite changement sur les clefs API dans  le core Jeedom >= 4.2.13, si vous n'avez pas de remontée d'alarmes dans les logs, il faut vérifier que la clé API du plugin est bien activé dans les paramètres de JEEDOM (Réglage/Système/Configuration/API)

# Stable prévue au 01/07/2022

- Détection automatiques des périphériques HIKVISION avec le protocole mDNS utilisé par le SADP Tool de Hik
- Mise en place de la rétention des fichiers JPG enregistrés dans le répertoire data du plugin ou gestion par le plugin camera
- Commandes PTZ (à voir si utile)
- Affichage du lien http pour se connecter à la caméra directement

# 20220329-stable (29 mars 2022)

- Merge de toutes les évolutions en beta depuis la dernière stable jusqu'à la beta du 20220329
- Activation / Désactivation de la détection de mouvement par type d'alarme (fielddetection, linedetection, VMD,...)
- Changement de l'image d'un périphérique avec fonction d'upload de l'image
- Reboot de la caméra via le plugin (droit nécessessaire)
- Intégration de la lib mDNS en vue de la détection automatique des device dans la prochaine stable

# 20220301-stable (01 mars 2022)

- Gestion du flux d'alarmes des Caméras et NVRs
- Affichge des capacités d'alarmes de l'équipement
- Affichage des infos systèmes

# En Beta
- **01/06/2022**  Mise à jour des dépendances et bascule sur NodeJS 16 conformément au prérequis de l'équipe jeedom 
- **29/03/2022**  Changement du nom du fichier de log pour hikvisioneventd pour coller au standard jeedom, Fix d'un probleme sur les tags XML vide
- **28/03/2022**  Ajout de la fonction Santé permettant de visualier d'un coup tous les devivces et d'afficher leur status (Connexion, CPU, mémoire,...)
- **21/03/2022**  Fix d'un problème sur les alarmes perte vidéo (videoloss) notament sur les NVR
- **18/03/2022**  Ajout de la fonction permettant d'activer/désactiver les alarmes par type (motiondetection, linedetection, fielddetection,...)
- **18/03/2022**  Optimisation des timeout réseau, Ajout d'une fonction permettant d'ignorer les enregistrements des images d'alarmes reçues
- **17/03/2022**  Inversion de la commande de heartbeat pour rester dans la norme hik. 1 si alarme, 0 si OK
- **15/03/2022**  Correction d'un probleme d'appel à l'API jeedom dans le cas ou jeedom intègre un certificat HTTPS et est configuré en HTTPS avec une IP LAN.
- **14/03/2022**  Correction d'un plantage dans certains cas dans le démon suite à l'appel de l'API Jeedom. Modification de quelques logs
- **08/03/2022**  Ajout d'une commande reboot du device + Amélioration lisibilité du code + correction de l'assignation de la pièce par défaut + Ajout fonctionnalité pour ignorer le message Jeedom de perte vidéo dans la configuration du plugin. Ajout la possibilité de changer l'image par défaut d'un équipement Hikvision. Intégration de la lib mDNS PHP en vue de la détection automatique des équipements hikvision.
- **07/03/2022**  Ajout des Fonctionnalités IO du device (capabilities) + Gestion de l'erreur 400 avec le code d'erreur HIKVISION + quelques traces de debug en plus
- **01/03/2022**  Ajout des Fonctionnalités du device (capabilities)
- **01/03/2022**  Amélioration du temps de démarrage du deamon et du retour sur l'enregistrement d'un device
- **25/02/2022**  Fix plusieurs problèmes notament sur Raspberry ou device jeedom lents. Affichage dans les logs des capabilities. Optimisation du code, Changement de la méthodologie de gestion des requetes HTTP(s) sur les devices HIK. Ajout d'un status de connexion et d'un status du deamon interrogés par le plugin. Ajut des icones documentations et community (attente du tag en cours de la team) dans le plugin. Fix définitif index région sur NVR
- **23/02/2022**  Ajout des infos systèmes du device hikvision dans la page config de l'équipement. Ajout des images d'équipements
- **22/02/2022**  Fix du probleme index Region sur les NVR. Protections contre les mauvaises saisies dans la config d'un équipement (espaces,...)
- **22/02/2022**  Ajout d'une fonction de lecture dans le device permettant de récupérer infos systèmes et possibilités de l'équipement. Ces données sont présentes dans les fichiers JSON/XML ajoutés dans le répertoire **/hikvisionevent/data/XXX/**. Fonctionnalité nécessaire afin de remonter les éléménts dans jeedom sur la prochaine beta et corriger le problème d'index des régions sur les NVR. La topologie NVR ou CAMERA sera également automatiquement détectée
- **19/02/2022**  Fix du probleme générant un message d'erreur dans les logs lors de la supression d'un équipement.
- **18/02/2022**  Fix du problème de communication avec le deamon lors d'une mise à jour du plugin
- **18/02/2022**  Mise à jour des commandes d'alarmes avec la répétitions de valeur et le returnstate à 0 (utile pour les NVR)
- **18/02/2022**  Ajout de la région dans les noms de fichier XML et JSON générés dans le répertoire data du plugin (il faut supprimer tout ce répertoire pour regénération)
- **18/02/2022**  Ajout de l'enregistrement des fichiers XML bruts reçus par l'API enregistrés dans le répertoire du plugin **/hikvisionevent/data/XXX/**
- **17/02/2022**  Modif. du nom des fichiers JSON enregistrés dans le répertoire du plugin **/hikvisionevent/data/XXX/**. Ajout des fichiers active/inactive à des fins de debug
- **17/02/2022**  Ajout des commandes "vu dernièrement" et "Chan X Dernière alarme"
- **17/02/2022**  Passage en public de la version beta après période de test avec des membres de la community
- **03/02/2022**  Réécriture d'une bibliotèque de gestion d'alarme avec l'API ISAPI
- **05/01/2022**  Création de la version beta
