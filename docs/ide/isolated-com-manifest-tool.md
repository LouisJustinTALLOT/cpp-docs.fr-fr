---
title: Propriétés COM isolé de l’outil Manifeste (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: a6188eeb53b4ffcd3eee754e88a8891310fb2d51
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738844"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM isolé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt;

Utilisez cette boîte de dialogue pour spécifier des options **COM isolé** pour [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pour accéder à cette boîte de dialogue de page de propriétés, ouvrez les pages de propriétés pour votre projet ou votre feuille de propriétés. Développez le nœud **Outil Manifeste** sous **Propriétés communes**, puis sélectionnez **COM isolé**.

## <a name="task-list"></a>Liste des tâches

- [Guide pratique pour générer des applications isolées afin de consommer des composants COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)

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
[Outil Manifeste, page de propriétés](../ide/manifest-tool-property-pages.md)<br>
[Utilisation des propriétés de projet](../ide/working-with-project-properties.md)
