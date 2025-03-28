---
layout: default
lang: fr_FR
title: Plugin Hikvision Event
description: Documentation du plugin Hikvision Event
---

Présentation 
=======================

Ce plugin permet de récupérer les alarmes et d'exécuter des actions sur vos équipements Hikvision (et sous-marques).
Les fonctionnalités et infos systèmes (firmware, réference,...) du périphérique sont récupérées et affichées dans les pages équipements.
Pour la beta, le plugin ne gère que la remontée d'alarme. Les commandes actions et infos systèmes arriveront dans les futures versions.
Sont supportés dans la version stable :
- Toutes les **caméras** Hikvision et marques rebrandées
- Tous les **NVR** Hikvision et marques rebrandées
- Tous les évènements liés au système : accès illégal, Doublon d'IP, Problème réseau, Heartbeat, ouverture boitier...
- Personnalisation des images des périphériques dans jeedom pour remplace les images de base (IPDome, IPCamera ou NVR) par défaut automatiquement détectées
- Tous les évènements liés à la détection à proprement parlé suivant les modèles 
  - Détection audio (augmentation/baisse de volume,...)
  - Détection vidéo non intelligente :
    - Détection de mouvement vidéo (VMD)
    - Détection changement de scène
  - Détection intelligente avec la classification des régions/zones détectées ainsi que la cible (humain ou voiture sur les caméras compatibles)
    - Intrusion 
    - Franchissement de lignes
    - Entrée/Sortie dans une région
    - Apparition/Disparition de baggages/objets
    - Detection de visage
    - Tous les autres types de détection **sans exception**
- La date de la dernière alarme (et par channel pour les NVR)
- La gestion de la présence sur le réseau de la caméra via le heartbeat natif et non un simple ping
  Avec possibiité dans les options du plugin de désactiver la notification d'un message Jeedom lors d'une perte réseau
- La reception automatique d'image d'alarme dans le flux d'alarme sans snapshot - Fonctionne notament sur gamme AcuSense EASY IP 4
- L'activation/désactivation de la détection d'alarme par type d'alarme (linedetection, fielddetection, motion detection,...)
- Le reboot du device
- l'affichage d'une page santé regroupant toutes les périphériques, leurs consommations CPU, mémoire,...

**A venir en beta :**

- Création d'un lien avec le plugin caméra afin que l'équipement soit créé (si pas présent) dans le plugin caméra. Les images reçues du flux d'alarme ne seront plus enregistrés dans le répertoire data du plugin hikvisionevent mais dans le répertoire data du plugin caméra afin de profiter de la visualisation facile 
- Envoi dans un scnéario de l'image reçue dans le flux d'alarme (hors snapshot) et donc possibilité d'envoyer sur telegram par exemple
- La prise d'un snapshot si la fonction précédente n'est pas gérée dans le flux d'alarme des caméras
- La détection des URL des flux vidéo
- La gestion des commandes PTZ (sachant que ces commandes sont déjà présentes dans le plugin officiel caméra)
- La détection automatique des périphériques HIKVISION. **La librairie est déjà intégrée et les tests iniitiaux sont réalisés**
- Allumage lampe et déclenchement message sur les caméras équpées.

> Attention depuis le beta du 17/03/2022, la gestion de la commande info de heartbeat est inversée (0 si OK, 1 si alarme)

> Les **portiers Hikvision doorbell** ne sont pour l'instant pas supportés (des tests sont en cours)

> Attention, Suite changement sur les clefs API dans  le core Jeedom >= 4.2.13, si vous n'avez pas de remontée d'alarmes dans les logs, il faut vérifier que la clé API du plugin est bien activé dans les paramètres de JEEDOM (Réglage/Système/Configuration/API). Ce bug du core semble avoir été corrigé dans la 4.2.14.

> Suite à de nombreux tests, à titre perso et pro, je vous conseille les caméras de la série EASY IP 4 ACUSENSE (format bullet, mini-dôme ou turret dans différentes versions avec ou sans audio, avec ou sans LED Flash, avec ou sans la fonction ColourVU)

> Attention ce plugin n'a pas vocation à gèrer la lecture des flux vidéos RTSP et MJPEG, le plugin officiel caméra de **JEEDOM** prenant en charge à 100% cette fonction  de lecture vidéo pour Hikvision. En revanche, il est prévu dans une prochaine version que l'ajout d'une caméra dans le plugin **HIKVISIONEVENT** ajoute automatiquement le device dans le plugin caméra officiel. Cette opération sera automatique.

> Lors de l'enregistrement de l'équipement, si une connexion sur le flux d'alarme est déjà effective sur l'équipement, la connexion est **tuée** puis **relancée**.

> Si vous rencontrez un problème dans le support de votre équipement Hikvision, contactez moi pour analyse et correction (Cas extremement rares).

Configuration du plugin 
=======================

Paramètres
-----------------------

Après installation du plugin, il vous suffit de l’activer. Il n'y a aucune configuration particulière à faire.
Il est nécessaire de ne pas toucher aux paramètres du démon. Seul le port du démon peut être modifié si celui par défaut est déjà utilisé sur votre machine jeedom
Quelques options sont configurables :
- **Port du démon** qui sert à la communication entre le plugin et le démon (Il est recommandé de ne pas le modifier)
- **Durée de rétention des images** pour la durée ou le plugin conserve les images enregistrées dans le répertoire data du plugin (fonction à venir)
- **Pièce par défaut** pour un équipement nouvellement créé 
- **Ignorer le heartbeat** permet, si coché, de ne pas générer un message Jeedom en cas de perte de la connexion avec l'équipement (evenement videoloss hikvision)
- **Ignorer les images d'alarme**, si coché, permet de ne pas enregistrer sur disques les images reçues à travers le gestionnaire d'alarme hikvision

> Les caméras en version firmware > 5.5 envoi ce heartbeat toutes les 10 secondes. Si le firmware <= 5.5, le rafraichissement est toutes les 300ms. A date ces firmwares anciens (<=5.5) peuvent poser des soucis de plantage du démon tant le volume d'évènement est important. Pb pris en compte.

Il sera possible dans une version ultérieure de détecter automatiquement les périphériques Hikvision sur votre réseau local. 
Je réfléchis également à comment afficher les images de détection (pour les caméras qui prennent en charge cette fonction)

Il est également possible de réparer NodeJS le cas échéant.

Equipements
-----------------------

La configuration des équipements Hikvision est accessible à partir du menu **plugins** puis **Sécurité** puis **Hikvision Event**.
Vous retrouvez ici :

-   un bouton pour **ajouter** un équipement manuellement
-   un bouton pour **afficher** les paramètres du plugin
-   un bouton **Télécharger Image** qui vous permet d'uploader depuis votre PC l'image d'un équipement
-   un bouton **Santé** qui vous donne une vue d'ensemble de tous vos équipements à un moment donné
-   un bouton **Community** qui pointe sur le fil de discussion de ce plugin sur la community
-   un bouton **Documentation** qui pointe sur cette présente documentation
-   enfin en dessous vous retrouvez la liste de vos équipements Hikvision

![ListeDevice](https://user-images.githubusercontent.com/60837526/160214492-5438afb7-8ff3-472f-855b-212e29fc04b0.JPG)


En cliquant sur un de vos équipements vous arrivez sur la page configuration de votre équipement comprenant 2 onglets, équipement et commandes.

-   **Onglet Equipement** :
-   **Nom de l’équipement** : nom de votre équipement
-   **Activer** : permet de rendre votre équipement actif
-   **Visible** : le rend visible sur le dashboard
-   **Objet parent** : indique l’objet parent auquel appartient l’équipement
-   **Protocole** : Protocole (HTTPS recommandé) à utiliser pour la connexion à équipement Hikvision.
-   **IP** : l'IP de l'équipement Hikvision (doit être fixe sur votre réseau local) ou FQDN de type macamera.mondomaine.com
-   **Port** : Le port de l'équipement Hikvision (Généralement 80 pour HTTP et 443 pour HTTPS).

> Si vous avez modifié le port par défaut (80 ou 443) comme sur la capture ci-dessous sur votre device Hikvision, vous pouvez le modifier sur le plugin.

![network-ok](https://user-images.githubusercontent.com/60837526/153629872-6fe42bc2-6bce-4afb-ac7f-840899a85f14.JPG)

-   **Utilisateur** : Utilisateur de l'équipement Hikvision (Un utilisateur spécifique à l'API ISAPI est nécessaire avec les droits suffisants). Voir ci-dessous. 
> NB : L'utilisateur Admin n'est pas autorisé.
-	**Mot de passe** : Mot de passe de l'équipement Hikvision.
-	**Image** : Image alternative pour remplacer l'image par défaut d'un équipement. Peut être uploadée depuis le bouton **Télécharger Image** de la page principale du plugin. Il est conseillé de trouver une image PNG avec fond transparent pour que la liste reste cohérente avec le design Jeedom. La recherche d'image à fond transparent peut facilement être effectuée avec Google rubrique Image puis dans les paramètres avancés de la recherche, possibilité de spécifier les paramètres d'image (résolution, fond transparent,...)

Il n'est pas nécessaire d'activer pour le plugin dans le réseau avancé l'option **Hikvision-CGI athentification** ni **ONVIF** sauf si vous utilisez ces fonctionnalités par ailleurs. Elles sont en revanche **requise** (CGI) pour l'utilisation du périphérique dans le plugin caméra. L'option CGI semble activée par défaut sur les NVR.
> NB : Lors de l'enregistrement de l'équipement. Si une connexion en cours est déjà effective sur l'équipement, la connexion est **tuée** puis **relancée**.

Informations devices Hikvision
-----------------------
Une fois la configuration enregistrée. Le plugin lance la connexion au device. Si elle réussie (peut être assez long la 1ère fois), s'affichera dans la page config de l'équipements l'ensemble des informations systèmes et fonctionnalités remontées par le périphérique Hikvision (Firwmare, Hardware, Type, Ref, Numéro de série, Adresse MAC, évènements supportés,...)

![DeviceInfo-ok](https://user-images.githubusercontent.com/60837526/157261269-ced544df-f5ed-4b6d-8ab9-3d4a89fb8d36.JPG)

Commandes générées
-----------------------
Les commandes d'alarmes sont automatiquement créées au fil de leur arrivée. Elles sont de type info Binaire.
Pour les voir apparaitre dans le plugin, il faut que les évènements en question se déclenchent au moins une fois.
C'est pour cette raison, à moins de savoir précisément ce que vous souhaitez utiliser comme alarme et si vous souhaitez dans un premier temps toutes les obtenir, il est conseillé de toutes les activer sur votre équipement Hikvision. Cela créera les commandes dynamiquement dès que les alarmes sont déclenchées, faites votre marché dans **Jeedom**, puis désactiver sur la caméra celles que vous ne souhaitez pas utiliser. Cela vous évitera d'avoir trop de déclenchements dans l'application (gratuite) **HIK-CONNECT**.

> NB : Les commandes info d'alarmes sont créées avec un return state à 0 au bout de 1 minute par sécurité. La gestion de la répétition des valeurs est activée nativement par le plugin. Cela permet de redéclencher un scénario sur nouvelle alarme alors que la précédenrte n'est pas acquittée.

Autant de commandes info sont créées que de 
- **Canaux** : 1 pour les caméras, plusieurs pour les NVR
- **Type d'alarme** : fielddetection, linedetection, regionEntrance, unattendedBaggage, audioexception, facedetection, attendedBaggage, diskError, faceCapture, scenechangedetection, VMD, ... (Liste non exhaustive dépendante des caméras)
- **Region** : Généralement 4 possibles pour la plupart des évènements intelligents   numérotés de 1 à 4.
- **Target** : La cible détectée (human ou vehicule) pour les caméras prenant en charge cette fonction. (Notament la gamme Accusense Easy IP 4)

Par exemple, cette commande info binaire est créée : **Chan 1 regionEntrance Region 1 human**
Libre à vous de la renommer après coup.
Cela vous permet de faire des scénarios très précis. Par exemple : franchissement de ligne dans un sens par une voiture, arrivée d'un objet humain dans la région 2, détection intrusion humain dans zone 4,...

Voici un exemple de commandes créées automatiquement
![list-commands](https://user-images.githubusercontent.com/60837526/154374788-d1077072-fbf0-48e3-8ba7-52dc0d0c357a.JPG)

- Les évènements classiques (ou non intelligents) sont **VMD** (video motion detection) et **scenechangedetection** (detection changement de scene) n'ont pas de région. cette catégorie regroupe aussi des évènements systèmes (erreur disk, erreur login, detection audio,...)
- Les évènements intelligents comportent pour la plupart 4 régions configurables. Le plus utilisé est **fielddetection** et correspond à la détection intrusion. **linedetection** peut être aussi intéressant pour détecter l'entrée ou la sortie d'une voiture ou d'une personne. Les possibilités, en fonction des modèles de caméras, sont illimitées.

> NB : Les évènements intelligents sont plus robustes et plus fiables que les évènements simple. Par exemple la détection intrusion intelligente (fielddetection) par rapport à la détection de mouvement simple (VMD).

Il est nécessaire d'activer chaque évènement désiré et d'activer pour chaque la fonction **Avertir le centre de surveillance** tel indiqué sur la capture ci-dessous afini que les commandes soient crées à leur arrivée dans Jeedom.

Les **commandes action** Activer et Désactiver sont aussi ajoutées dynamiquement dès que l'alarme se présente. Il vous est maintenant possible d'activer ou désactiver  la détection en fonction du type souhaité (fielddetection, linedetection, ...). Pour cette fonction et pour éviter l'erreur 403 (privilège insuffisant), il est nécessaire d'activer les droits sur le device : **A distance : paramétrage**

![event-ok](https://user-images.githubusercontent.com/60837526/153620262-998acf82-b909-43b9-a281-8d7889c0554c.jpg)

En parallèle sont aussi créées les commandes :
- Heartbeat (état) du périphérique (0 si connecté, 1 si alarme)
- Dernière communication avec le device
- Dernière date d'alarme sur chaque channel (Sur les NVR, cela permet d'avoir une date par caméra) - Il s'agit du timestamp remonté par le device et non la date/heure de jeedom
- Reboot du périphérique (Il est nécessaire d'avoir mis les bons droits dans la création du user. Voir config gestion des utilisateurs ci-dessous) cf **A distance : arrêter/redémarrer**

Fonctionnement du flux d'Alarme 
=======================
La connexion au flux d'alarme du périphérique est lancé lors du démarrage du démon et lors de l'enregistrement d'un périphérique (postSave).
A la connexion initiale, le périphérique est intérogé et retourne ses infos et ses fonctionnalités.
En cas de perte de connexion sur le flux d'alarme, celui ci est relancé automatiquement toutes les 30 secondes.

> NB : Si lors de l'intérrogation initiale (deamon_sart et postsave), le périphérique n'est pas joignable, alors la connexion au flux d'alarme est abandonnée et ne sera pas relancée.

**Paramètrage des caméras ou NVR Hikvision**
=====================================================

Système - Config système
-----------------------

![systemvca](https://user-images.githubusercontent.com/60837526/153620665-1a235508-fef7-402a-830f-5885f31251da.JPG)

Système - Sécurité
-----------------------
Basculer de l'authentification DIGEST en DIGEST/BASIC le RTSP (vous servira pour le plugin camera jeedom ou autre NVR) et Authentification WEB (nécessaire pour ce présent plugin)

![Systemauth](https://user-images.githubusercontent.com/60837526/153620948-7e186621-75ad-48b8-9817-31c77bfc9a57.JPG)

Système - Gestion des utilisateurs
-----------------------
Créer un utilisateur dédié au plugin. La capture représente le minimum requis pour le plugin. Si vous souhaitez pouvoir visualiser la caméra dans le plugin caméra natif jeedom, il est nécessaire de rajouter les droits audio et vidéo en lecture.

Si vous souhaitez pouvoir redemarrer l'équipement avec la commande action, les droits démarrer/arrêter son nécessaire

![6df8070b5fa3a0fecfe25af38ce14c084489e467](https://user-images.githubusercontent.com/60837526/158280256-9d59451a-cdb4-44f9-9d66-3a3322b9530b.png)

Idem pour l'activation des alarmes, il est nécessaire d'avoir le droit **A distance : paramétrage**

![systemusers-ok](https://user-images.githubusercontent.com/60837526/153629554-f0580c4d-8169-4b90-b28d-21d46745b5bf.JPG)

Network - Avancé
-----------------------
Cette partie ne concerne pas directement ce plugin et n'est donc pas nécessaire.
En revanche elle est nécessaire si vous souhaitez intégrer la caméra dans le plugin caméra jeedom natif.
La liste des utilisateurs à cet endroit là ne concerne que le protocole **ONVIF**, si vous ne l'utiliser pas (pas nécessaire dans le plugin caméra), inutile de crééer des utilisateurs ONVIF.

![networkadvanced-ok](https://user-images.githubusercontent.com/60837526/153638744-d15962ed-45c4-4f75-8edd-1a1fe2d43c7e.JPG)

Cas particuliers des NVR
=============================

Notes d'application
-----------------------

Les NVR Hikvision sont pleinement supportés par ce plugin.
En revanche suivant la gamme, NI-K (light) et NI-I (plus haut de gamme), toutes les fonctionnalités ne sont pas prises en charge de la même façon que sur une caméra. C'est lié à 100% de ce que remonte l'API ISAPI Hikvision. Exemples :
- Sur les NI-K, les régions de détection ne remontent pas. Elles sont prises en charge dans les NI-I suite à une correction d'index éronnée dans l'API
- Sur l'ensemble des NVR l'évènement correspondant à la fin d'une alarme n'est jamais remonté au plugin. La "retombée" à 0 de la commande ad-hoc est gérée par la fonction du core returnstate. Info remise donc à 0 au bout d'une minute. Sur une caméra, cette sécurité est tout de même présente mais la fin d'alarme est gérée par les évènements reçus à travers l'API. La gestion est donc plus fine sur une caméra ou la dureé d'une alarme peut être de quelques secondes seulement contrairement à un NVR ou la durée de l'alarme sera forcément de 60 secondes au minimum. Cela peut avoir son importance.
- l'alarme illAccess (Login éronné sur la web interface du device) n'est pas remonté sur certains NVR lights Ni-K
- Les targets de détection (voiture et/ou humain) ne sont jamais remontés à ma connaissance à travers ISAPI depuis les NVR vers Jeedom. si vous souhaitez pouvoir gérer ce type d'évènements plus finement, il est nécessaire, en plus du NVR, de rentrer vos caméras en tant qu'équipement du plugin JEEDOM.

Config système complémentaire
-----------------------
A venir

**Portiers doorbell Hikvision**
==============================================
A venir suivant compatibilité.
authentification DIGEST obligatoire sur certains modèles.
flux alertStream vide et non bloquant


