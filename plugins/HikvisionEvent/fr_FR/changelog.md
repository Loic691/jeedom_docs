---
layout: default
lang: fr_FR
title: Plugin Hikvision Event Home - Changelog
description: Changelog du plugin Hikvision Event
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour pour la compatibilité Jeedom V4

# En Beta
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

# Stable prévue au 01/03/2022

- Gestion du flux d'alarmes des caméras et NVR
- Génération des commandes infos binaires en automatique au fil de l'arrivée des évènements
- 

# Stable prévue au 01/04/2022

- Activation / Désactivation de la détection de mouvement par type d'alarme (fielddetection, linedetection, VMD,...)
- Affichge des capacités d'alarmes de l'équipement
- Affichage des infos systèmes
- Reboot de la caméra via le plugin
- Mise en place de la rétention des fichiers JPG enregistrés dans le répertoire data du plugin
- Commandes PTZ (à voir si utile)

