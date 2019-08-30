---
title: Référence C++ de page de propriétés de projet Windows-Visual Studio
ms.date: 08/28/2019
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: c9fd4fc00e86e0660972fc0bd37b66b2fea02ee0
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177470"
---
# <a name="windows-c-project-property-page-reference"></a>Référence C++ de la page de propriétés du projet Windows

Dans Visual Studio, vous spécifiez les options du compilateur et de l’éditeur de liens, les chemins d’accès aux fichiers et d’autres paramètres de génération via les pages de propriétés du projet. Les propriétés et les pages de propriétés disponibles varient selon le type de projet. Par exemple, un projet Makefile a une page de propriétés NMake, qui n’est pas présente dans un projet de console MFC ou Win32. Pour ouvrir les **pages de propriétés**, choisissez**Propriétés** du **projet** > dans le menu principal, ou cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Propriétés**. Les fichiers individuels ont également des pages de propriétés qui vous permettent de définir des options de compilation et de génération uniquement pour ce fichier. L’illustration suivante montre les pages de propriétés d’un projet MFC.

![Pages de propriétés C++ du projet](media/example-prop-page.png)

Cette section fournit une référence rapide pour les pages de propriétés elles-mêmes. Les options et les paramètres exposés dans les pages de propriétés sont documentés plus complètement dans leurs propres rubriques et sont liés depuis les rubriques de la page de propriétés. Pour plus d’informations sur les propriétés de projet, consultez [définir C++ des propriétés de compilation et de compilation dans Visual Studio](../working-with-project-properties.md).

Pour les pages de propriétés dans les projets Linux, consultez Référence de la [page de propriétés Linux C++ ](../../linux/prop-pages-linux.md).

## <a name="in-this-section"></a>Dans cette section

- [Général, page de propriétés (Projet)](general-property-page-project.md)
- [Général, page de propriétés (Fichier)](general-property-page-file.md)
- [Page de propriétés avancé](advanced-property-page.md)
- [Répertoires VC++, page de propriétés](vcpp-directories-property-page.md)
- [Éditeur de liens, page de propriétés](linker-property-pages.md)
- [Outil Manifeste, page de propriétés](manifest-tool-property-pages.md)
- [HLSL, page de propriétés](hlsl-property-pages.md)
- [Ligne de commande, pages de propriétés](command-line-property-pages.md)
- [Étape de génération personnalisée, page de propriétés : Général](custom-build-step-property-page-general.md)
- [Ajout de références](../adding-references-in-visual-cpp-projects.md)
- [Ressources managées, page de propriétés](managed-resources-property-page.md)
- [MIDL, page de propriétés](midl-property-pages.md)
- [NMake, page de propriétés](nmake-property-page.md)
- [Ressources, page de propriétés](resources-property-pages.md)
- [Références web, page de propriétés](web-references-property-page.md)
- [XML Data Generator Tool, page de propriétés](xml-data-generator-tool-property-page.md)
- [Outil Générateur de documents XML, page de propriétés](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer et supprimer les dépendances d’un projet](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[Guide pratique : créer et modifier des configurations](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Référence C++ de la page de propriétés Linux](../../linux/prop-pages-linux.md)
