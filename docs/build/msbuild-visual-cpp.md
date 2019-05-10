---
title: MSBuild sur la ligne de commande - C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220564"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild sur la ligne de commande - C++

En règle générale, nous vous recommandons d’utiliser Visual Studio pour définir les propriétés du projet et appeler le système MSBuild. Toutefois, vous pouvez utiliser la **MSBuild** outil directement à partir de l’invite de commandes. Le processus de génération est contrôlé par les informations contenues dans un fichier projet (.vcxproj) que vous pouvez créer et modifier. Le fichier projet spécifie les options de génération en fonction de génération phases, les conditions et les événements. En outre, vous pouvez spécifier zéro ou plus de la ligne de commande *options* arguments.

> **msbuild.exe** [ *project_file* ] [ *options* ]

Utilisez le **/target** (ou **/t**) et **cette propriété** (ou **/p**) options de ligne de commande pour remplacer les propriétés spécifiques et les cibles spécifié dans le fichier projet.

Des fonctions essentielles du fichier projet consiste à spécifier un *cible*, qui est une opération spécifique appliquée à votre projet et que les entrées et sorties qui sont requis pour effectuer cette opération. Un fichier de projet peut spécifier une ou plusieurs cibles, ce qui peuvent inclure une cible par défaut.

Chaque cible se compose d’une séquence d’un ou plusieurs *tâches*. Chaque tâche est représentée par une classe .NET Framework qui contient une commande exécutable. Par exemple, le [tâche CL](/visualstudio/msbuild/cl-task) contient le [cl.exe](reference/compiling-a-c-cpp-program.md) commande.

Un *paramètre de tâche* est une propriété de la tâche de classe et représentant généralement une option de ligne de commande de la commande exécutable. Par exemple, le `FavorSizeOrSpeed` paramètre de la `CL` tâche correspond à la **/Os** et **/Ot** options du compilateur.

Paramètres de tâche supplémentaires prennent en charge l’infrastructure MSBuild. Par exemple, le `Sources` paramètre de tâche spécifie un ensemble de tâches qui peuvent être consommées par d’autres tâches. Pour plus d’informations sur les tâches MSBuild, consultez [référence des tâches](/visualstudio/msbuild/msbuild-task-reference).

La plupart des tâches requièrent des entrées et sorties, telles que les noms de fichiers, chemins d’accès et chaîne, numériques ou booléennes paramètres. Par exemple, une entrée commune est le nom d’un fichier de source .cpp à compiler. Un paramètre d’entrée important est une chaîne qui spécifie la configuration de build et la plateforme, par exemple, « débogage\|Win32 ». Entrées et sorties sont spécifiées par un ou plusieurs XML défini par l’utilisateur `Item` éléments contenus dans un `ItemGroup` élément.

Un fichier projet peut également spécifier défini par l’utilisateur *propriétés* et `ItemDefinitionGroup` *éléments*. Propriétés et éléments forment des paires nom/valeur qui peuvent être utilisées en tant que variables dans la build. Le composant de nom d’une paire définit un *macro*, et le composant de valeur déclare la *valeur de macro*. Une macro de propriété est accessible à l’aide de $(*nom*), de notation et d’une macro d’élément est accessible à l’aide de %(*nom*) notation.

Autres éléments XML dans un fichier projet peuvent tester des macros, puis conditionnellement définir la valeur d’une macro ou contrôler l’exécution de la build. Noms de macros et les chaînes littérales peuvent être concaténées pour générer des constructions telles que d’un chemin d’accès et nom de fichier. Sur la ligne de commande, le **cette propriété** option définit ou substitue une propriété de projet. Impossible de référencer les éléments sur la ligne de commande.

Le système MSBuild peut exécuter de façon conditionnelle une cible avant ou après une autre cible. En outre, le système peut générer une cible, selon que les fichiers que la cible consomme sont plus récents que les fichiers qu’elle émet.

Pour plus d’informations sur MSBuild, consultez :

- [MSBuild](/visualstudio/msbuild/msbuild) concepts de vue d’ensemble de MSBuild.

- [MSBuild Référence](/visualstudio/msbuild/msbuild-reference) informations de référence sur le système MSBuild.

- [Référence du schéma de fichier de projet](/visualstudio/msbuild/msbuild-project-file-schema-reference) répertorie les éléments de schémas XML MSBuild, ainsi que leurs attributs et les éléments parents et enfants. Notez en particulier le [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [cible](/visualstudio/msbuild/target-element-msbuild), et [tâche](/visualstudio/msbuild/task-element-msbuild) éléments.

- [Référence de ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference) décrit les arguments de ligne de commande et les options que vous pouvez utiliser avec msbuild.exe.

- [Référence de tâches](/visualstudio/msbuild/msbuild-task-reference) tâches MSBuild décrit. Notez en particulier les tâches suivantes, qui sont spécifiques à Visual C++ : [BSCMAKE, tâche](/visualstudio/msbuild/bscmake-task), [tâche CL](/visualstudio/msbuild/cl-task), [CPPClean, tâche](/visualstudio/msbuild/cppclean-task), [tâche LIB](/visualstudio/msbuild/lib-task), [lier tâche](/visualstudio/msbuild/link-task), [tâche MIDL](/visualstudio/msbuild/midl-task), [MT, tâche](/visualstudio/msbuild/mt-task), [RC, tâche](/visualstudio/msbuild/rc-task), [setenv, tâche](/visualstudio/msbuild/setenv-task), [VCMessage, tâche](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>Dans cette section

|Terme|Définition|
|----------|----------------|
|[Procédure pas à pas : Utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Montre comment créer un Visual Studio C++ à l’aide de projet **MSBuild**.|
|[Guide pratique pour utiliser des événements de génération dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Montre comment spécifier une action qui se produit à une étape particulière dans la build : avant le début de la génération ; avant le démarrage d’étape de liaison ; ou après la fin du build.|
|[Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Montre comment ajouter une étape définie par l’utilisateur à la séquence de génération.|
|[Guide pratique pour ajouter des outils de génération personnalisée à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Montre comment associer un outil de génération d’un fichier particulier.|
|[Guide pratique pour intégrer les outils personnalisés dans les propriétés du projet](how-to-integrate-custom-tools-into-the-project-properties.md)|Montre comment ajouter des options pour un outil personnalisé aux propriétés du projet.|
|[Guide pratique pour modifier le framework cible et l’ensemble d’outils de plateforme](how-to-modify-the-target-framework-and-platform-toolset.md)|Montre comment compiler un projet pour plusieurs infrastructures ou ensembles d’outils.|

## <a name="see-also"></a>Voir aussi

[Utiliser le jeu d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)
