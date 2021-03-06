---
description: 'En savoir plus sur : page de propriétés NMake'
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
ms.openlocfilehash: 58256ad8542e7d411769efb661970f9c41797ec3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196800"
---
# <a name="nmake-property-page"></a>NMake (page de propriétés)

La page de propriétés **NMake** vous permet de spécifier des paramètres de build pour les projets NMake. (NMAKE est l’implémentation Microsoft de [Make](https://wikipedia.org/wiki/Make_(software)).)

Pour plus d’informations sur les projets NMake, consultez [Création d’un projet Makefile](creating-a-makefile-project.md). Pour les projets MakeFile non-Windows, consultez [Propriétés du projet Makefile (Linux c++)](../../linux/prop-pages/makefile-linux.md), [général propriétés du projet (Makefile Android C++)](/visualstudio/cross-platform/general-makefile-android-prop-page) ou [Propriétés NMAKE (Android c++)](/visualstudio/cross-platform/nmake-android-prop-page).

La page de propriétés **NMake** contient les propriétés suivantes.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

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

Pour plus d’informations sur l’accès à la page de propriétés **NMAKE** , consultez [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md).

Pour plus d’informations sur l’accès par programmation aux membres de cet objet, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les pages de propriétés de projet C++](property-pages-visual-cpp.md)<br>
