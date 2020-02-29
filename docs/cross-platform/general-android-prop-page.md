---
title: Propriétés générales du projet (Android C++)
ms.date: 10/23/2017
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
f1_keywords:
- VC.Project.VCConfiguration.Android.OutputDirectory
- VC.Project.VCConfiguration.Android.IntermediateDirectory
- VC.Project.VCConfiguration.Android.TargetName
- VC.Project.VCConfiguration.Android.TargetExt
- VC.Project.VCConfiguration.Android.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.Android.BuildLogFile
- VC.Project.VCConfiguration.Android.PlatformToolset
- VC.Project.VCConfiguration.Android.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: 694e69e063f73830c21976bd0615cf4d1d99b368
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177576"
---
# <a name="general-project-properties-android-c"></a>Propriétés générales du projet (Android C++)

Propriété | Description | Choices
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif au répertoire des fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Nom de la cible | Spécifie un nom de fichier généré par ce projet.
Extension de la cible | Spécifie une extension de fichier générée par ce projet. (Exemple : *.exe* ou *.dll*)
Extensions à supprimer lors du nettoyage | Spécification de caractères génériques délimités par des points-virgules pour les fichiers du répertoire intermédiaire à supprimer durant le nettoyage ou la regénération.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Ensemble d'outils de plateforme | Spécifie l’ensemble d’outils utilisé pour générer la configuration actuelle ; s’il n’est pas défini, l’ensemble d’outils par défaut est utilisé
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)** : bibliothèque dynamique ( *.so*)<br>**Bibliothèque statique (.a)** : bibliothèque statique ( *.a*)<br>**Utilitaire** : utilitaire<br>**Makefile** : fichier makefile<br>
Niveau d’API cible | Niveau d’API du Kit de développement natif (NDK) Android ciblé par cette configuration.
Utilisation de STL | Spécifie la bibliothèque C++ standard à utiliser pour cette configuration. | **Bibliothèque minimale runtime C++ (system)**<br>**Bibliothèque statique runtime C++ (gabi++_static)**<br>**Bibliothèque partagée runtime C++ (gabi++_shared)**<br>**Bibliothèque statique runtime STLport (stlport_static)**<br>**Bibliothèque partagée runtime STLport (stlport_shared)**<br>**Bibliothèque statique GNU STL (gnustl_static)**<br>**Bibliothèque partagée GNU STL (gnustl_shared)**<br>**Bibliothèque statique LLVM libc++ (c++_static)**<br>**Bibliothèque partagée LLVM libc++ (c++_shared)**<br>
Mode Thumb | Générez du code qui s’exécute pour une microarchitecture Thumb. Applicable uniquement à l’architecture ARM. | **Thumb**<br>**ARM**<br>**Désactivé**<br>
