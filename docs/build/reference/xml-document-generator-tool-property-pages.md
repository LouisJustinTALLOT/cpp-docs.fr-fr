---
title: Outil Générateur de documents XML, page de propriétés
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: c99677d7fc53ae3343e15e54997fe0101322fbcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316156"
---
# <a name="xml-document-generator-tool-property-pages"></a>Outil Générateur de documents XML, page de propriétés

La page de propriétés Outil Générateur de documents XML expose les fonctionnalités de xdcmake.exe. xdcmake.exe fusionne des fichiers .xdc en fichier .xml quand votre code source contient des commentaires de documentation et que [/doc (Traiter les commentaires de documentation) (C/C++)](doc-process-documentation-comments-c-cpp.md) est spécifié. Consultez [Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md) pour plus d’informations sur l’ajout de commentaires de documentation dans le code source.

> [!NOTE]
>  Les options de xdcmake.exe dans l’environnement de développement (pages de propriétés) diffèrent des options de xdcmake.exe quand celui-ci est utilisé sur la ligne de commande. Pour plus d’informations sur l’utilisation de xdcmake.exe à partir de la ligne de commande, consultez [Informations de référence sur XDCMake](xdcmake-reference.md).

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Suppression de la bannière de démarrage**

   Supprimez le message de copyright.

- **Fichiers de document supplémentaires**

   Répertoires supplémentaires dans lesquels vous voulez que le système de projet recherche les fichiers .xdc. xdcmake recherche toujours les fichiers .xdc générés par le projet. Vous pouvez spécifier plusieurs répertoires.

- **Fichier de document de sortie**

   Nom et emplacement du répertoire du fichier de sortie .xml. Consultez [macros courantes pour générer des propriétés et les commandes](common-macros-for-build-commands-and-properties.md) pour plus d’informations sur l’utilisation de macros pour spécifier des emplacements de répertoire.

- **Dépendances de bibliothèque de documents**

   Si votre projet a une dépendance sur un projet .lib dans la solution, vous pouvez traiter les fichiers .xdc du projet .lib dans les fichiers .xml du projet actuel.

## <a name="see-also"></a>Voir aussi

[Référence de page de propriété de projet C++](property-pages-visual-cpp.md)