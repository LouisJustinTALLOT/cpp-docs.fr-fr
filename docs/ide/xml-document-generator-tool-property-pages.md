---
title: Outil Générateur de documents XML, page de propriétés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee18e32d1aaf2a9035b425cb3c3ef5e2db15145
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718807"
---
# <a name="xml-document-generator-tool-property-pages"></a>Outil Générateur de documents XML, page de propriétés
La page de propriétés Outil Générateur de documents XML expose les fonctionnalités de xdcmake.exe. xdcmake.exe fusionne des fichiers .xdc en fichier .xml quand votre code source contient des commentaires de documentation et que [/doc (Traiter les commentaires de documentation) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) est spécifié. Consultez [Balises recommandées pour les commentaires de documentation](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) pour plus d’informations sur l’ajout de commentaires de documentation dans le code source.  
  
> [!NOTE]
>  Les options de xdcmake.exe dans l’environnement de développement (pages de propriétés) diffèrent des options de xdcmake.exe quand celui-ci est utilisé sur la ligne de commande. Pour plus d’informations sur l’utilisation de xdcmake.exe à partir de la ligne de commande, consultez [Informations de référence sur XDCMake](../ide/xdcmake-reference.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
- **Suppression de la bannière de démarrage**

   Supprimez le message de copyright.  
  
- **Fichiers de document supplémentaires**

   Répertoires supplémentaires dans lesquels vous voulez que le système de projet recherche les fichiers .xdc. xdcmake recherche toujours les fichiers .xdc générés par le projet. Vous pouvez spécifier plusieurs répertoires.  
  
- **Fichier de document de sortie**

   Nom et emplacement du répertoire du fichier de sortie .xml. Consultez [Macros courantes pour les propriétés et les commandes de génération](../ide/common-macros-for-build-commands-and-properties.md) pour plus d’informations sur l’utilisation de macros afin de spécifier des emplacements de répertoire.  
  
- **Dépendances de bibliothèque de documents**

   Si votre projet a une dépendance sur un projet .lib dans la solution, vous pouvez traiter les fichiers .xdc du projet .lib dans les fichiers .xml du projet actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés](../ide/property-pages-visual-cpp.md)   
 [Pages de propriétés](../ide/property-pages-visual-cpp.md)