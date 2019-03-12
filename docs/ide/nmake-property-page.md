---
title: NMake, page de propriétés (Windows C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: 18d32dd85c39586576686942968a3f6e1735337d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749895"
---
# <a name="nmake-property-page"></a>NMake (page de propriétés)

La page de propriétés **NMake** vous permet de spécifier des paramètres de build pour les projets NMake.

Pour plus d’informations sur les projets NMake, consultez [Création d’un projet Makefile](../ide/creating-a-makefile-project.md). Pour les projets MakeFile autres que Windows, consultez [Projet Makefile, propriétés (Linux C++)](../linux/prop-pages/makefile-linux.md), [Propriétés générales du projet (Makefile Android C++)](/visualstudio/cross-platform/general-makefile-android-prop-page) ou [Propriétés NMake (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).

La page de propriétés **NMake** contient les propriétés suivantes.

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Ligne de commande Build**

   Spécifie la commande à exécuter quand **Générer** est sélectionné dans le menu **Générer**.

- **Ligne de commande Rebuild All**

   Spécifie la commande à exécuter quand **Regénérer tout** est sélectionné dans le menu **Générer**.

- **Ligne de commande Clean**

   Spécifie la commande à exécuter quand **Nettoyer** est sélectionné dans le menu **Générer**.

- **Sortie**

   Spécifie le nom du fichier qui doit contenir la sortie de la ligne de commande. Par défaut, ce nom de fichier est basé sur le nom du projet.

- **Définitions de préprocesseur**

   Spécifie toutes les définitions de préprocesseur que les fichiers sources utilisent. La valeur par défaut est déterminée par la plateforme et la configuration actuelles.

- **Chemin de recherche Include**

   Spécifie les répertoires où le compilateur recherche des fichiers Include.

- **Fichiers Include forcés**

   Spécifie les fichiers que le préprocesseur traite automatiquement même s’ils ne sont pas inclus dans les fichiers projet.

- **Chemin de recherche des assemblys**

   Spécifie les répertoires où le .NET Framework effectue des recherches quand il essaye de résoudre des assemblys .NET.

- **Utilisation forcée des assemblys**

   Spécifie les assemblys que le .NET Framework traite automatiquement.

- **Options supplémentaires**

   Spécifie tous les commutateurs du compilateur supplémentaires que doit utiliser IntelliSense lors de l’analyse de fichiers C++.

Pour plus d’informations sur l’accès à la page de propriétés **NMake**, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

Pour plus d’informations sur l’accès par programmation aux membres de cet objet, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../ide/property-pages-visual-cpp.md)<br>
[Guide pratique pour Activer IntelliSense pour des projets Makefile](../ide/how-to-enable-intellisense-for-makefile-projects.md)
