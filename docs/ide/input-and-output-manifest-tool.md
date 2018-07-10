---
title: Propriétés Entrée et sortie de l’outil Manifeste (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs:
- C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15be7636188bb670febd7875974d683c1d78360f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331556"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Entrée et sortie, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de &lt;NomProjet&gt;
Utilisez cette boîte de dialogue pour spécifier des options d’entrée et de sortie pour [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Pour accéder à cette boîte de dialogue de page de propriétés, ouvrez les pages de propriétés pour votre projet ou votre feuille de propriétés. Développez le nœud **Outil Manifeste** sous **Propriétés de configuration**, puis sélectionnez **Entrée et sortie**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Fichiers manifeste supplémentaires**  
 Utilise l’option **/manifest** pour spécifier les chemins complets des fichiers manifeste supplémentaires que l’outil Manifeste traitera ou fusionnera. Les chemins complets sont délimités par un point-virgule.  
  
 **Manifestes de ressource d’entrée**  
 Utilise l’option **/inputresource** pour spécifier le chemin complet d’une ressource de type RT_MANIFEST, à entrer dans l’outil Manifeste. Le chemin peut être suivi de l’ID de ressource spécifié. Exemple :  
  
 `dll_with_manifest.dll;#1`  
  
 L’ID de ressource est facultatif et a par défaut la valeur CREATEPROCESS_MANIFEST_RESOURCE_ID dans winuser.h.  
  
 **Incorporer le manifeste**  
 **Oui** spécifie que le système de projet incorporera le fichier manifeste d’application dans l’assembly.  
  
 **Non** spécifie que le système de projet créera le fichier manifeste d’application en tant que fichier autonome.  
  
 **Fichier manifeste de sortie**  
 Spécifie le nom du fichier manifeste de sortie. Cette propriété est facultative quand un seul fichier manifeste est traité par l’outil Manifeste.  
  
 **Fichier de ressources du manifeste**  
 Spécifie les fichiers de ressources de sortie utilisés pour incorporer le manifeste dans la sortie de projet.  
  
 **Génération de fichiers catalogue**  
 Utilise l’option **/makecdfs** pour spécifier que l’outil Manifeste générera des fichiers de définition de catalogue (fichiers .cdf), qui sont utilisés pour faire des catalogues.  
  
 **Génération du manifeste à partir de ManagedAssembly**  
 Génère un manifeste à partir d’un assembly managé. (**-managedassemblyname:***fichier*).  
  
 **Suppression des éléments de dépendance**  
 Utilisé avec l’option **-managedassembly**. Cette balise supprime la génération des éléments de dépendance dans le manifeste final.  
  
 **Génération des indicateurs de catégorie**  
 Utilisé avec l’option **-managedassembly**. Cette balise entraîne la génération des indicateurs de catégorie.  
  
 **Prise en charge DPI**  
 Spécifie si l’application prend en charge DPI. Par défaut, le paramètre a la valeur **Oui** pour les projets MFC et **Non** pour les autres projets parce que seuls les projets MFC présentent une prise en charge DPI intégrée. Vous pouvez remplacer le paramètre par **Oui** si vous ajoutez du code pour gérer différents paramètres DPI. Votre application peut apparaître floue ou petite si vous la définissez comme prenant en charge DPI quand ce n’est pas le cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Pages de propriétés de l’outil Manifeste](../ide/manifest-tool-property-pages.md)   
 [Utilisation des propriétés de projet](../ide/working-with-project-properties.md)   