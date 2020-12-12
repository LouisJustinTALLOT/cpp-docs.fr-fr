---
description: 'En savoir plus sur : informations de référence sur les pages de propriétés de projet Windows C++'
title: Informations de référence sur les pages de propriétés de projet Windows C++-Visual Studio
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
ms.openlocfilehash: 30e8f33f09242779529d368fbafc72ee66a0264f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225737"
---
# <a name="windows-c-project-property-page-reference"></a>Informations de référence sur la page de propriétés de projet Windows C++

Dans Visual Studio, vous spécifiez les options du compilateur et de l’éditeur de liens, les chemins d’accès aux fichiers et d’autres paramètres de génération via les pages de propriétés du projet. Les propriétés et les pages de propriétés disponibles varient selon le type de projet. Par exemple, un projet Makefile a une page de propriétés NMake, qui n’est pas présente dans un projet de console MFC ou Win32. Pour ouvrir les **pages de propriétés**, choisissez  >  **Propriétés** du projet dans le menu principal, ou cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Propriétés**. Les fichiers individuels ont également des pages de propriétés qui vous permettent de définir des options de compilation et de génération uniquement pour ce fichier. L’illustration suivante montre les pages de propriétés d’un projet MFC.

![Pages de propriétés pour un projet C++](media/example-prop-page.png)

Cette section fournit une référence rapide pour les pages de propriétés elles-mêmes. Les options et les paramètres exposés dans les pages de propriétés sont documentés plus complètement dans leurs propres rubriques et sont liés depuis les rubriques de la page de propriétés. Pour plus d’informations sur les propriétés de projet, consultez [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md).

Pour les pages de propriétés dans les projets Linux, consultez Référence de la [page de propriétés C++ Linux](../../linux/prop-pages-linux.md).

## <a name="in-this-section"></a>Dans cette section

- [Général, page de propriétés (projet)](general-property-page-project.md)
- [Général, page de propriétés (Fichier)](general-property-page-file.md)
- [Page de propriétés avancé](advanced-property-page.md)
- [Page de propriétés des répertoires VC + +](vcpp-directories-property-page.md)
- [Pages de propriétés de l’éditeur de liens](linker-property-pages.md)
- [Pages de propriétés de l’outil manifeste](manifest-tool-property-pages.md)
- [Pages de propriétés HLSL](hlsl-property-pages.md)
- [Pages de propriétés ligne de commande](command-line-property-pages.md)
- [Étape de génération personnalisée, page de propriétés : général](custom-build-step-property-page-general.md)
- [Ajout de références](../adding-references-in-visual-cpp-projects.md)
- [Ressources managées (page de propriétés)](managed-resources-property-page.md)
- [Pages de propriétés MIDL](midl-property-pages.md)
- [NMake (page de propriétés)](nmake-property-page.md)
- [Pages de propriétés des ressources](resources-property-pages.md)
- [Page de propriétés références Web](web-references-property-page.md)
- [Outil XML Data Generator Tool (page de propriétés)](xml-data-generator-tool-property-page.md)
- [Page de propriétés de l’outil générateur de documents XML](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Voir aussi

[Comment : créer et supprimer des dépendances de projet](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[Guide pratique pour créer et modifier des configurations](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Référence de la page de propriétés C++ Linux](../../linux/prop-pages-linux.md)
