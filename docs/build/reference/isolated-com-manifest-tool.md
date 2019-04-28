---
title: Outil manifeste COM isolé propriétés
ms.date: 12/10/2018
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 2fda169ecf304373d27d699bf313bde124dc399f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269711"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM isolé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt;

Utilisez cette boîte de dialogue pour spécifier des options **COM isolé** pour [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pour accéder à cette boîte de dialogue de page de propriétés, ouvrez les pages de propriétés pour votre projet ou votre feuille de propriétés. Développez le nœud **Outil Manifeste** sous **Propriétés communes**, puis sélectionnez **COM isolé**.

## <a name="task-list"></a>Liste des tâches

- [Guide pratique pour générer des applications isolées afin de consommer des composants COM](../how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Fichier bibliothèque de types**

   Utilise l’option /tlb pour spécifier le nom du fichier bibliothèque de types (fichier .tlb) que l’outil Manifeste utilise pour générer le fichier manifeste.

- **Fichier de script d’inscription**

   Utilise l’option /rgs pour spécifier le nom du fichier de script d’inscription (fichier .rgs) que l’outil Manifeste utilise pour générer le fichier manifeste.

- **Nom de fichier du composant**

   Utilise l’option /dll pour spécifier le nom de la ressource que l’outil Manifeste génère. Vous devez entrer une valeur pour cette propriété quand des valeurs sont spécifiées pour **Fichier bibliothèque de types** ou **Fichier de script d’inscription**.

- **Fichier de remplacement**

   Utilise l’option /replacements pour spécifier le chemin complet au fichier qui contient des valeurs pour les chaînes remplaçables dans le fichier .rgs.

## <a name="see-also"></a>Voir aussi

[Applications isolées](/windows/desktop/SbsCs/isolated-applications)<br>
[ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)<br>
[Outil Manifeste, page de propriétés](manifest-tool-property-pages.md)<br>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)
