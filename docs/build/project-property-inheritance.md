---
title: Héritage de propriété dans les projets Visual Studio - C++
ms.date: 12/10/2018
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 7e6e2ec4e4f1999639a1b0a0d7ce35873736e5e3
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220434"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Héritage de propriété dans les projets Visual Studio

Le système de projet Visual Studio est basé sur MSBuild, qui définit les formats de fichier et les règles de génération de projets d’aucune sorte. MSBuild gère une grande partie de la complexité de génération pour plusieurs plateformes et configurations, mais il faut comprendre un peu son fonctionnement. C’est particulièrement important si vous voulez définir des configurations personnalisées ou créer des ensembles de propriétés réutilisables à partager et importer dans plusieurs projets.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Le fichier .vcxproj, les fichiers .props et les fichiers .targets

Propriétés de projet sont stockées directement dans le fichier projet (*.vcxproj) ou dans d’autres fichiers .targets ou .props que les importations du fichier projet et qui fournissent des valeurs par défaut. Pour Visual Studio 2015, ces fichiers se trouvent dans **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Pour Visual Studio 2017, ces fichiers se trouvent dans **\\Program Files (x86)\\Microsoft Visual Studio\\2017\\_edition_\\Common7\\IDE\\VC\\VCTargets**, où _edition_ est l’édition de Visual Studio installée. Les propriétés sont également stockées dans les fichiers .props personnalisés que vous pouvez ajouter à votre propre projet. Nous recommandons vivement de ne PAS modifier ces fichiers manuellement et d’utiliser à la place les pages de propriétés dans l’IDE pour modifier toutes les propriétés, en particulier celles qui résultent d’un héritage, à moins d’avoir une très bonne compréhension de MSBuild.

Comme indiqué précédemment, la même propriété pour la même configuration peut avoir une valeur différente dans ces différents fichiers. Quand vous générez un projet, le moteur MSBuild évalue le fichier projet et tous les fichiers importés dans un ordre bien défini (décrit ci-dessous). Comme chaque fichier est évalué, toutes les valeurs de propriété définies dans ce fichier remplacent les valeurs existantes. Les valeurs qui ne sont pas spécifiées sont héritées des fichiers qui ont été évalués précédemment. Par conséquent, quand vous définissez une propriété dans les pages de propriétés, faites bien attention à l’endroit où vous la définissez. Si vous définissez une propriété sur « X » dans un fichier .props, mais qu’elle est définie sur « Y » dans le fichier projet, le projet est généré avec la propriété définie sur « Y ». Si la même propriété est définie sur « Z » sur un élément de projet, par exemple, un fichier .cpp, le moteur MSBuild utilise la valeur « Z ». 

Voici l’arborescence d’héritage de base :

1. Paramètres par défaut de l’ensemble d’outils MSBuild CPP (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, qui est importé par le fichier .vcxproj.)

2. Feuilles de propriétés

3. Fichier .vcxproj. (peut substituer les paramètres par défaut et les paramètres de feuille de propriétés.)

4. Métadonnées d'élément

> [!TIP]
> Sur une page de propriétés, une propriété dans `bold` est définie dans le contexte actuel. Une propriété en police normale est héritée.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Afficher un fichier de projet développé avec toutes les valeurs importées

Il est parfois utile d'afficher le fichier développé pour déterminer comment une valeur de propriété donnée est héritée. Pour afficher la version développée, entrez la commande suivante à une invite de commandes Visual Studio. (Remplacez les espaces réservés des noms de fichiers par ceux que vous voulez utiliser.)

**msbuild /pp:** *temp* **.txt** *mon_application* **.vcxproj**

Les fichiers projet développés peuvent être volumineux et difficiles à comprendre si MSBuild ne vous est pas familier. Voici la structure de base d'un fichier projet :

1. Propriétés de projet fondamentales, qui ne sont pas exposées dans l'environnement IDE.

2. Importation de Microsoft.cpp.default.props, qui définit des propriétés de base et indépendantes des ensembles d'outils.

3. Propriétés de configuration globales (exposées comme les propriétés par défaut **PlatformToolset** et **Project** dans la page **Configuration générale**. Ces propriétés déterminent l'ensemble d'outils et les feuilles de propriétés intrinsèques importés dans Microsoft.cpp.props à l'étape suivante.

4. Importation de Microsoft.cpp.props, qui définit la plupart des paramètres par défaut du projet.

5. Importation de toutes les feuilles de propriétés, y compris les fichiers .user. Ces feuilles de propriétés peuvent tout remplacer sauf les propriétés par défaut **PlatformToolset** et **Project**.

6. Les propriétés restantes de la configuration du projet. Ces valeurs peuvent remplacer celles définies dans les feuilles de propriétés.

7. Éléments (fichiers) avec leurs métadonnées. Il s’agit toujours du dernier mot dans les règles d’évaluation MSBuild, même s’ils se produisent avant d’autres propriétés et importations.

Pour plus d’informations, consultez l’article [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configurations de build

Une configuration est simplement un groupe arbitraire de propriétés qui porte un nom. Visual Studio fournit des configurations Debug et Release, et chacune définit des propriétés différentes pour une build debug ou release. Vous pouvez utiliser le **Gestionnaire de configuration** pour définir des configurations personnalisées et regrouper de manière pratique des propriétés pour une version particulière de build. 

Pour obtenir une meilleure idée des configurations de build, ouvrez **Gestionnaire de propriétés** en choisissant **vue &#124; Gestionnaire de propriétés** ou **vue &#124; Windows autres &#124; Gestionnaire de propriétés**  en fonction de vos paramètres. **Gestionnaire de propriétés** a des nœuds pour chaque paire plateforme/configuration dans le projet. Chacun de ces nœuds contient d’autres nœuds pour les feuilles de propriétés (fichiers .props) qui définissent des propriétés spécifiques pour cette configuration.

![Gestionnaire de propriétés](media/property-manager.png "Gestionnaire de propriétés")

Si vous accédez au volet Général dans les Pages de propriétés et définir la propriété du jeu de caractères de « Ne pas définir « au lieu de « Utiliser Unicode », puis cliquez sur **OK**, Gestionnaire de propriétés affichera aucun **prise en charge Unicode** feuille de propriétés la configuration actuelle, mais il seront toujours disponibles pour d’autres configurations.

Pour plus d’informations sur le Gestionnaire de propriétés et les feuilles de propriétés, consultez [les paramètres de projet de Visual Studio C++ partage ou resuse](create-reusable-property-configurations.md).

> [!TIP]
> Le fichier .user est une fonctionnalité héritée et nous vous recommandons de la supprimer pour que les propriétés restent correctement groupées en fonction de la configuration/plateforme.



