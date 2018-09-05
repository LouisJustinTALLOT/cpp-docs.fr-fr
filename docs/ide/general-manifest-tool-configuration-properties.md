---
title: Outil Manifeste, Propriétés de configuration (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef1eb1c0c1ee8c9fb2814bc7cd808ea2e524b8a4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200331"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Général, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt;
Utilisez cette boîte de dialogue pour spécifier des options générales pour [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Pour accéder à cette boîte de dialogue de page de propriétés, ouvrez les pages de propriétés de votre projet ou votre feuille de propriétés. Développez le nœud **Outil Manifeste** sous **Propriétés de configuration**, puis sélectionnez **Général**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Suppression de la bannière de démarrage**  
 **Oui (/nologo)** spécifie que les données de copyright standard de Microsoft n’apparaîtront pas au démarrage de l’outil Manifeste. Utilisez cette option pour supprimer les sorties dont vous ne voulez pas dans les fichiers journaux, quand vous exécutez mt.exe dans le cadre d’un processus de génération ou à partir d’un environnement de génération.  
  
 **Sortie des commentaires**  
 **Oui (/verbose)** spécifie que des informations de build supplémentaires seront affichées pendant la génération du manifeste.  
  
 **Identité d’assembly**  
 Utilise l’option /identity afin de spécifier une chaîne d’identité qui comprend les attributs pour [l’élément \<assemblyIdentity>](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Une chaîne d’identité commence par la valeur de l’attribut `name`, suivie des paires *attribut* = *valeur*. Les attributs dans une chaîne d’identité sont délimités par une virgule.  
  
 Voici un exemple de chaîne d’identité :  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Pages de propriétés de l’outil Manifeste](../ide/manifest-tool-property-pages.md)   
 [Utilisation des propriétés de projet](../ide/working-with-project-properties.md)   