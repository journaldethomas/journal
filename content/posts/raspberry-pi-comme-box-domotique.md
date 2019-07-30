---
layout: post
title: "Raspberry Pi comme box domotique"
categories: domotique
img: image-3.png
date: 2019-07-01T13:51:20+02:00
draft: false
---
On a vu précédemment pourquoi domotiser son appartement. Pour commencer cette nouvelle série d'articles je voulais commencer par le début : la box domotique. Il existe sur le marché de nombreux fabricants et même les grandes enseignes de bricolage propose aujourd'hui leur box. Il faut souvent compter autour des 200-300 euros pour une telle box. Ne voulant pas investir beaucoup d'argent dans un premier temps je suis partie sur une solution bien moins chère basée sur un [Raspberry Pi](https://fr.wikipedia.org/wiki/Raspberry_Pi). Cet ordinateur, qui a la taille d'une carte de crédit, est destiné à encourager l'apprentissage de la programmation informatique mais pas d'inquiétude il n'y a rien de bien compliqué. L'autre intérêt d'utiliser un raspberry est que vous ne confier pas vos données à quelqu'un d'autre. Je vais essayer de vous détailler ici les différentes étapes qui permettront d'utiliser un raspberry pi comme box domotique.

Matériel nécessaire :

un [Raspberry Pi](https://www.amazon.fr/gp/product/B01CD5VC92/ref=as_li_tl?ie=UTF8&camp=1642&creative=6746&creativeASIN=B01CD5VC92&linkCode=as2&tag=tc0e4d-21&linkId=a7081466d92bed2ff33b03bab4bebebb) 3 Model B Quad Core CPU 1.2 GHz 1 Go RAM;
une carte microSD de 4Go minimum sur laquelle le système d'exploitation sera installé;
une Alimentation 5v de 2,5A minimum pour le Raspberry Pi 3;
un clavier et une souris;
un cable éthernet pour pouvoir se connecter au réseau;
un cable HDMI pour vous simplifier la vie et suivre l'installation sur un écran.

Etape 1 : installer Raspbian

Cette première étape se fait à partir d'un poste de travail classique. Télécharger tout d'abord l'image de la [dernière version de Raspbian](https://www.raspberrypi.org/downloads/raspbian/). Ensuite que vous soyez MAC ou PC, je vous conseille de télécharger et d'installer l'outil etcher qui vous permettra de copier cette image sur votre carte SD. J'ai mis du temps à trouver un outil fonctionnel sur MAC mais avec [Etcher](https://etcher.io/) je n'ai eu aucun problème pour créer la carte SD. Et c'est tout simple : vous sélectionnez l'image Raspbian, la carte SD et vous cliquez sur Flash. Après quatre ou cinq minutes c'est prêt.

Une fois le copie terminée, votre carte SD est maintenant prête à être insérée dans votre raspberry pi. Connectez y une souris, un clavier, le cable ethernet et un écran puis brancher le cable d'alimentation. Le Raspberry Pi s'allume et va booter sur la carte SD.

Etape 2 : configuration du système

C'est la partie un peu technique mais c'est tellement plus simple de faire les prochaines étapes en ligne de commande que je vous encourage à le faire. Je vas essayer d'être le plus concis possible. Ouvrez un Terminal via l'icône adéquate en haut à gauche de l'écran.

Et tapez la commande suivante :

sudo raspi-config

Je vous recommande de régler dans un premier temps vos paramètres de localisation tel que langage (fr_FR.UTF-8 UTF-8), le fuseau horaire (Europe / Paris) et surtout le clavier (French / Azerty). Vous trouverez ces options dans Localisation Options. Il est très important de modifier le clavier dès les premières étapes car par défaut il est en qwerty et cela pourrait vous poser quelques soucis par la suite. Notamment pour changer le mot de passe par défaut. Par défaut le username et le mot de passe sont respectivement pi et raspberry. La modification de ce dernier par un mot de passe connu seulement de vous est fortement recommandé afin de sécuriser un peu plus votre raspberry pi.

Dans Interfacing Options il faut ensuite activer la connexion en ssh. En effet cela vous permettra de ne plus avoir à brancher un écran à votre Rasperry Pi. Vous pourrez vous connecter à votre machine à partir de votre poste de travail principal ce qui peut s'avérer très pratique. Gardons à l'esprit que nous voulons utiliser notre raspberry pi comme box domotique et qu'il ne sera pas forcément accessible pour y brancher un écran.

Et enfin dans Advanced Options il faut étendre le file system principal via Expand Filesystem. Cela permet d'utiliser tout l'espace disque disponible de votre carte SD.

Il nous reste plus qu'à sélectionner finish et reboot pour la prise en compte de ces changements. A partir de là vous pouvez vous passer d'écran et vous connecter en ssh à votre raspberry pi à partir de votre poste de travail principal. C'est l'option que j'ai choisi pour continuer de configurer mon raspberry en ouvrant un terminal sur mon mac principal.

Une fois connecté, il faut s'assurer que le système est à jour en tapant les commandes suivantes :

sudo apt-get update
sudo apt-get upgrade

Ces commandes peuvent être assez longues à exécuter. Il ne vous restera ensuite plus qu'à rebooter votre raspberry pour que toutes les modifications soient prises en compte.

sudo reboot

Ca y est votre raspberry est désormais prêt pour accueillir votre application domotique. C'est ce que nous verrons d'ici quelques jours.

