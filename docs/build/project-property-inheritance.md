---
title: Héritage des propriétés dans les projets Visual Studio – C++
description: Fonctionnement de l’héritage des propriétés dans les projets Visual Studio C++ natifs (MSBuild).
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 17b23426f70bb2d306491e538d30cffc0f202362
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919213"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Héritage des propriétés dans les projets Visual Studio

Le système de projet Visual Studio native est basé sur MSBuild. MSBuild définit des formats de fichier et des règles pour générer des projets de tout type. Il gère la plus grande partie de la complexité de la création pour plusieurs configurations et plateformes. Vous y trouverez des informations utiles pour comprendre son fonctionnement. Cela est particulièrement important si vous souhaitez définir des configurations personnalisées. Ou, pour créer des ensembles de propriétés réutilisables que vous pouvez partager et importer dans plusieurs projets.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Fichier .vcxproj, fichiers .props et fichiers .targets

::: moniker range="msvc-140"

Les propriétés de projet sont stockées dans plusieurs fichiers. Certaines sont stockées directement dans le *`.vcxproj`* fichier projet. D’autres proviennent d' *`.targets`* autres *`.props`* fichiers ou que le fichier projet importe et qui fournissent des valeurs par défaut. Vous trouverez les fichiers projet Visual Studio 2015 dans un dossier spécifique aux paramètres régionaux sous le répertoire de base, *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\v140`* .

::: moniker-end

::: moniker range="msvc-150"

Les propriétés de projet sont stockées dans plusieurs fichiers. Certaines sont stockées directement dans le *`.vcxproj`* fichier projet. D’autres proviennent d' *`.targets`* autres *`.props`* fichiers ou que le fichier projet importe et qui fournissent des valeurs par défaut. Vous trouverez les fichiers projet Visual Studio 2017 dans un dossier spécifique aux paramètres régionaux sous le répertoire de base, *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* .

::: moniker-end

::: moniker range=">=msvc-160"

Les propriétés de projet sont stockées dans plusieurs fichiers. Certaines sont stockées directement dans le *`.vcxproj`* fichier projet. D’autres proviennent d' *`.targets`* autres *`.props`* fichiers ou que le fichier projet importe et qui fournissent des valeurs par défaut. Vous trouverez les fichiers projet Visual Studio dans un dossier spécifique aux paramètres régionaux sous le répertoire de base, *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>`* . Le `<version>` est spécifique à la version de Visual Studio. Il s’agit *`v160`* de Visual Studio 2019.

::: moniker-end

Les propriétés sont également stockées dans tous les *`.props`* fichiers personnalisés que vous pouvez ajouter à votre propre projet. Nous vous recommandons vivement de *ne pas* modifier ces fichiers manuellement. Utilisez plutôt les pages de propriétés dans l’IDE pour modifier toutes les propriétés, en particulier celles qui participent à l’héritage, à moins que vous n’ayez une connaissance approfondie de MSBuild et des *`.vcxproj`* fichiers.

Comme indiqué précédemment, une même propriété pour une même configuration peut avoir une valeur différente dans ces différents fichiers. Quand vous générez un projet, le moteur MSBuild évalue le fichier projet et tous les fichiers importés dans un ordre bien défini qui est décrit plus loin. Comme chaque fichier est évalué, toutes les valeurs de propriété définies dans ce fichier remplacent les valeurs existantes. Les valeurs qui ne sont pas spécifiées sont héritées des fichiers qui ont été évalués précédemment. Lorsque vous définissez une propriété avec des pages de propriétés, il est également important de faire attention à l’emplacement où vous la définissez. Si vous affectez la valeur « X » à une propriété dans un *`.props`* fichier, mais que la propriété a la valeur « y » dans le fichier projet, le projet est généré avec la propriété définie sur « y ». Si la même propriété est définie sur « Z » sur un élément de projet, tel qu’un *`.cpp`* fichier, le moteur MSBuild utilise la valeur « z ».

Voici l’arborescence d’héritage de base :

1. Paramètres par défaut de l’ensemble d’outils MSBuild CPP (le *`Microsoft.Cpp.Default.props`* fichier dans le répertoire de base, qui est importé par le *`.vcxproj`* fichier.)

1. Feuilles de propriétés

1. *`.vcxproj`* txt. (Ce fichier peut remplacer les paramètres par défaut et les paramètres de la feuille de propriétés.)

1. Métadonnées d'élément

> [!TIP]
> Dans une page de propriétés, une propriété en **gras** est définie dans le contexte actuel. Une propriété en police normale est héritée.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Afficher un fichier projet développé avec toutes les valeurs importées

Il est parfois utile d'afficher le fichier développé pour déterminer comment une valeur de propriété donnée est héritée. Pour afficher la version développée, entrez la commande suivante à une invite de commandes Visual Studio. (Remplacez les espaces réservés des noms de fichiers par ceux que vous voulez utiliser.)

> **msbuild /pp:**_temp_**.txt** _mon_application_**.vcxproj**

Les fichiers projet développés peuvent être volumineux et difficiles à comprendre, sauf si vous êtes familiarisé avec MSBuild. Voici la structure de base d'un fichier projet :

1. Propriétés de projet fondamentales, qui ne sont pas exposées dans l’IDE.

1. Importation de *`Microsoft.cpp.default.props`* , qui définit des propriétés de base, indépendantes des ensembles d’outils.

1. Propriétés de configuration globales (exposées en tant que propriétés par défaut de **PlatformToolset** et **Project** dans la page **configuration générale** . Ces propriétés déterminent l’ensemble d’outils et les feuilles de propriétés intrinsèques importés dans *`Microsoft.cpp.props`* à l’étape suivante.

1. Importation de *`Microsoft.cpp.props`* , qui définit la plupart des paramètres par défaut du projet.

1. Importation de toutes les feuilles de propriétés, y compris les *`.user`* fichiers. Ces feuilles de propriétés peuvent remplacer tout sauf les propriétés par défaut **PlatformToolset** et **Project** .

1. Le reste des propriétés de configuration de projet. Ces valeurs peuvent remplacer celles définies dans les feuilles de propriétés.

1. Éléments (fichiers) avec leurs métadonnées. Ces éléments sont toujours le dernier mot dans les règles d’évaluation MSBuild, même s’ils se produisent avant d’autres propriétés et importations.

Pour plus d’informations, consultez [propriétés MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configurations de build

Une configuration est simplement un groupe arbitraire de propriétés qui porte un nom. Visual Studio fournit des configurations Debug et Release. Chaque définit de manière appropriée différentes propriétés pour une version Debug ou une version Release. Vous pouvez utiliser la **Configuration Manager** pour définir des configurations personnalisées. Ils constituent un moyen pratique de regrouper des propriétés pour une version spécifique de la Build.

Pour obtenir une meilleure idée des configurations de build, ouvrez **Gestionnaire de propriétés** . Vous pouvez l’ouvrir en choisissant **afficher > gestionnaire de propriétés** ou **afficher > autres > Windows Gestionnaire de propriétés** , en fonction de vos paramètres. **Gestionnaire de propriétés** a des nœuds pour chaque paire de configuration et de plateforme dans le projet. Sous chacun de ces nœuds se trouvent des nœuds pour les feuilles de propriétés ( *`.props`* fichiers) qui définissent des propriétés spécifiques pour cette configuration.

![Gestionnaire de propriétés](media/property-manager.png "Gestionnaire de propriétés")

Par exemple, vous pouvez accéder au volet général dans les pages de propriétés. Remplacez la valeur de la propriété jeu de caractères par « non défini » au lieu de « utiliser Unicode », puis cliquez sur **OK** . La Gestionnaire de propriétés affiche désormais aucune feuille de propriétés de **prise en charge Unicode** . Elle est supprimée pour la configuration actuelle, mais elle existe toujours pour d’autres configurations.

Pour plus d’informations sur le Gestionnaire de propriétés et les feuilles de propriétés, consultez [Partager ou réutiliser des paramètres de projet Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Le *`.user`* fichier est une fonctionnalité héritée. Nous vous recommandons de le supprimer pour conserver les propriétés correctement regroupées en fonction de la configuration et de la plateforme.
