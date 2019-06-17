---
title: Général, propriétés (projet Linux C++) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: ce3683f11d80c253195b751b5eed364fbc04b68a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821284"
---
# <a name="general-properties-linux-c"></a>Général, propriétés (Linux C++)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Property | Description | Options
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif vers le répertoire de fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Nom de la cible | Spécifie un nom de fichier généré par ce projet.
Extension cible | Spécifie une extension de fichier générée par ce projet. (Exemple : .a)
Extensions à supprimer lors du nettoyage | Spécification de caractères génériques séparés par des points-virgules pour les fichiers du répertoire intermédiaire à supprimer durant le nettoyage ou la regénération.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Ensemble d'outils de plateforme | Spécifie l’ensemble d’outils utilisé pour générer la configuration actuelle ; s’il n’est pas défini, l’ensemble d’outils par défaut est utilisé
Machine de build distante | Machine ou appareil cible à utiliser pour la génération, le déploiement et le débogage à distance. **Visual Studio 2019 version 16.1** Une autre machine pour le débogage peut être spécifiée dans la page [Débogage](debugging-linux.md).
Répertoire racine de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant.
Répertoire de projet de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant du projet.
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)**  : bibliothèque dynamique (.so)<br>**Bibliothèque statique (.a)**  : bibliothèque statique (.a)<br>**Application (.out)**  : application (.out)<br>**Makefile** : fichier makefile<br>
Utilisation de STL | Spécifie la bibliothèque C++ standard à utiliser pour cette configuration. | **Bibliothèque standard C++ GNU partagée**<br>**Bibliothèque standard C++ GNU statique (-static)**<br>

::: moniker-end

