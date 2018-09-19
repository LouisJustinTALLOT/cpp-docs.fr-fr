---
title: Avancé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a86489e18220e674f48222ef1590b61d7c5defcf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716524"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Avancé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt;
Utilisez cette boîte de dialogue pour spécifier des options avancées pour [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Pour accéder à cette boîte de dialogue de page de propriétés, ouvrez les pages de propriétés de votre projet ou de votre feuille de propriétés. Développez le nœud **Outil Manifeste** sous **Propriétés de configuration**, puis sélectionnez **Avancé**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface

- **Mettre à jour les fichiers à hacher**

   Utilise l’option /hashupdate pour spécifier que l’outil Manifeste va calculer le hachage des fichiers spécifiés dans les éléments `<file>`, puis mettre à jour les attributs de hachage avec la valeur calculée.  
  
- **Chemin de recherche de mise à jour des fichiers à hacher**

   Spécifie le chemin de recherche des fichiers qui sont référencés dans les éléments `<file>`. Cette option utilise également l’option /hashupdate.  
  
## <a name="see-also"></a>Voir aussi  
 [\<file>, élément](/visualstudio/deployment/file-element-clickonce-application)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Pages de propriétés de l’outil Manifeste](../ide/manifest-tool-property-pages.md)   
 [Utilisation des propriétés de projet](../ide/working-with-project-properties.md)   