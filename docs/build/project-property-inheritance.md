---
title: Héritage des propriétés dans les projets Visual Studio – C++
description: Fonctionnement de l’héritage immobilier dans les projets natifs (MSBuild) Visual Studio C.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328474"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Héritage des propriétés dans les projets Visual Studio

Le système de projet natif Visual Studio est basé sur MSBuild. MSBuild définit les formats de fichiers et les règles pour la construction de projets de toute nature. Il gère la majeure partie de la complexité de la construction pour de multiples configurations et plates-formes. Vous trouverez utile de comprendre comment cela fonctionne. C’est particulièrement important si vous voulez définir des configurations personnalisées. Ou, pour créer des ensembles réutilisables de propriétés que vous pouvez partager et importer dans plusieurs projets.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Fichier .vcxproj, fichiers .props et fichiers .targets

Les propriétés du projet sont*`.vcxproj`* stockées directement *`.targets`* *`.props`* dans le dossier du projet () soit dans d’autres fichiers ou fichiers que le projet importe et qui fournissent des valeurs par défaut. Pour Visual Studio 2015, ces *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* fichiers sont situés dans . Pour Visual Studio 2017, ces *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* fichiers *`<edition>`* sont situés dans , où est l’édition Visual Studio installé. Dans Visual Studio 2019, ces *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* fichiers sont situés dans . Les propriétés sont *`.props`* également stockées dans tous les fichiers personnalisés que vous pourriez ajouter à votre propre projet. Nous vous recommandons fortement de ne pas modifier ces fichiers manuellement. Utilisez plutôt les pages de propriété dans l’IDE pour modifier toutes les propriétés, en particulier ceux qui participent à l’héritage, sauf si vous avez une compréhension profonde de MSBuild.

Comme indiqué précédemment, une même propriété pour une même configuration peut avoir une valeur différente dans ces différents fichiers. Quand vous générez un projet, le moteur MSBuild évalue le fichier projet et tous les fichiers importés dans un ordre bien défini (décrit ci-dessous). Comme chaque fichier est évalué, toutes les valeurs de propriété définies dans ce fichier remplacent les valeurs existantes. Toutes les valeurs qui ne sont pas spécifiées sont héritées de fichiers qui ont été évalués plus tôt. Lorsque vous définissez une propriété avec des pages de propriété, il est également important de prêter attention à l’endroit où vous la définissez. Si vous définissez une propriété *`.props`* à "X" dans un fichier, mais la propriété est définie à "Y" dans le dossier du projet, alors le projet va construire avec la propriété définie à "Y". Si la même propriété est définie à "Z" *`.cpp`* sur un élément de projet, comme un fichier, alors le moteur MSBuild utilisera la valeur "Z".

Voici l’arborescence d’héritage de base :

1. Paramètres par défaut de la MSBuild CPP Toolset (.. 'Program Files’MSBuild-Microsoft.Cpp’v4.0-Microsoft.Cpp.Default.props, qui est *`.vcxproj`* importé par le fichier.)

1. Feuilles de propriétés

1. *`.vcxproj`* Fichier. (peut substituer les paramètres par défaut et les paramètres de feuille de propriétés.)

1. Métadonnées d'élément

> [!TIP]
> Sur une page de propriété, une propriété en **gras** est définie dans le contexte actuel. Une propriété en police normale est héritée.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Afficher un fichier projet développé avec toutes les valeurs importées

Il est parfois utile d'afficher le fichier développé pour déterminer comment une valeur de propriété donnée est héritée. Pour afficher la version développée, entrez la commande suivante à une invite de commandes Visual Studio. (Remplacez les espaces réservés des noms de fichiers par ceux que vous voulez utiliser.)

> **msbuild /pp:**_temp_**.txt** _mon_application_**.vcxproj**

Les fichiers de projet élargis peuvent être importants et difficiles à comprendre à moins que vous ne connaissiez MSBuild. Voici la structure de base d'un fichier projet :

1. Propriétés de projet fondamentales, qui ne sont pas exposées dans l’IDE.

1. Importation *`Microsoft.cpp.default.props`* de , qui définit certaines propriétés de base, indépendantes des outils.

1. Propriétés Global Configuration (exposées sous le nom **de PlatformToolset** et **Project** propriétés par défaut sur la page **Configuration Générale.** Ces propriétés déterminent dans quelle ensemble d’outils et feuilles intrinsèques de propriété sont importées dans *`Microsoft.cpp.props`* l’étape suivante.

1. Importation *`Microsoft.cpp.props`* de , qui définit la plupart des défauts de projet.

1. Importation de toutes les *`.user`* feuilles de propriété, y compris les fichiers. Ces feuilles de propriété peuvent remplacer tout sauf les propriétés par défaut **PlatformToolset** et **Project.**

1. Le reste des propriétés de configuration du projet. Ces valeurs peuvent remplacer celles définies dans les feuilles de propriétés.

1. Éléments (fichiers) avec leurs métadonnées. Ces éléments sont toujours le dernier mot dans les règles d’évaluation MSBuild, même si elles se produisent avant d’autres propriétés et importations.

Pour plus d’informations, voir [MSBuild Properties](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configurations de build

Une configuration est simplement un groupe arbitraire de propriétés qui porte un nom. Visual Studio propose des configurations Debug et Release. Chacune définit différentes propriétés de manière appropriée pour une construction ou une version de débagé. Vous pouvez utiliser le **gestionnaire de configuration** pour définir des configurations personnalisées. Ils sont un moyen pratique de regrouper les propriétés pour une saveur spécifique de construction.

Pour avoir une meilleure idée des configurations de construction, ouvert **gestionnaire de propriété**. Vous pouvez l’ouvrir en choisissant **View > Property Manager** ou View > Other Windows > Property **Manager**, en fonction de vos paramètres. **Gestionnaire de propriété** a des nœuds pour chaque paire de configuration et de plate-forme dans le projet. Sous chacun de ces nœuds sont*`.props`* des nœuds pour les feuilles de propriété (fichiers) qui définissent certaines propriétés spécifiques pour cette configuration.

![Gestionnaire de propriétés](media/property-manager.png "Gestionnaire de propriétés")

Par exemple, vous pouvez vous rendre à la vitre générale des Pages de la Propriété. Modifier la propriété De définir de caractère à "Pas défini" au lieu de "Utiliser Unicode", puis cliquez **sur OK**. Le gestionnaire immobilier ne montre plus de fiche de propriété **Unicode Support.** Il est supprimé pour la configuration actuelle, mais il est toujours là pour d’autres configurations.

Pour plus d’informations sur le Gestionnaire de propriétés et les feuilles de propriétés, consultez [Partager ou réutiliser des paramètres de projet Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Le *`.user`* fichier est une fonctionnalité héritée. Nous vous recommandons de le supprimer, de garder les propriétés correctement regroupées en fonction de la configuration et de la plate-forme.
