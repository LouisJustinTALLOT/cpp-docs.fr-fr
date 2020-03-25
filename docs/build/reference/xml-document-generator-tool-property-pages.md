---
title: Pages de propriétés Outil Générateur de documents XML
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: 9f10ddf98c238120750e72644779a6ad74af2d1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171630"
---
# <a name="xml-document-generator-tool-property-pages"></a>Pages de propriétés Outil Générateur de documents XML

La page de propriétés Outil Générateur de documents XML expose les fonctionnalités de xdcmake.exe. xdcmake.exe fusionne des fichiers .xdc en fichier .xml quand votre code source contient des commentaires de documentation et que [/doc (Traiter les commentaires de documentation) (C/C++)](doc-process-documentation-comments-c-cpp.md) est spécifié. Consultez [Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md) pour plus d’informations sur l’ajout de commentaires de documentation dans le code source.

> [!NOTE]
>  Les options de xdcmake.exe dans l’environnement de développement (pages de propriétés) diffèrent des options de xdcmake.exe quand celui-ci est utilisé sur la ligne de commande. Pour plus d’informations sur l’utilisation de xdcmake.exe à partir de la ligne de commande, consultez [Informations de référence sur XDCMake](xdcmake-reference.md).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Suppression de la bannière de démarrage**

   Supprime le message de copyright.

- **Fichiers de document supplémentaires**

   Répertoires supplémentaires dans lesquels vous voulez que le système de projet recherche les fichiers .xdc. xdcmake recherche toujours les fichiers .xdc générés par le projet. Vous pouvez spécifier plusieurs répertoires.

- **Fichier de document de sortie**

   Nom et emplacement du répertoire du fichier de sortie .xml. Pour plus d’informations sur l’utilisation des macros pour spécifier des emplacements de répertoire [, consultez macros courantes pour les propriétés et les commandes de génération](common-macros-for-build-commands-and-properties.md) .

- **Dépendances de bibliothèque de documents**

   Si votre projet a une dépendance sur un projet .lib dans la solution, vous pouvez traiter les fichiers .xdc du projet .lib dans les fichiers .xml du projet actuel.

## <a name="see-also"></a>Voir aussi

[C++Référence de la page de propriétés du projet](property-pages-visual-cpp.md)
