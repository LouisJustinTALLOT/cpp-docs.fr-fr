---
description: 'En savoir plus sur : MSBuild sur la ligne de commande-C++'
title: MSBuild sur la ligne de commande-C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 9d78c50b398b0ad97cfd75727fdb4219677c546b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179848"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild sur la ligne de commande-C++

En général, nous vous recommandons d’utiliser Visual Studio pour définir les propriétés du projet et appeler le système MSBuild. Toutefois, vous pouvez utiliser l’outil **MSBuild** directement à partir de l’invite de commandes. Le processus de génération est contrôlé par les informations contenues dans un fichier projet (. vcxproj) que vous pouvez créer et modifier. Le fichier projet spécifie des options de génération en fonction des étapes de génération, des conditions et des événements. En outre, vous pouvez spécifier zéro ou plusieurs arguments d' *options* de ligne de commande.

> **msbuild.exe** [ *project_file* ] [ *options* ]

Utilisez les options de ligne de commande **/target** (ou **/t**) et **/Property** (ou **/p**) pour remplacer des propriétés et des cibles spécifiques qui sont spécifiées dans le fichier projet.

Une fonction essentielle du fichier projet consiste à spécifier une *cible*, qui est une opération particulière appliquée à votre projet, ainsi que les entrées et les sorties qui sont requises pour effectuer cette opération. Un fichier projet peut spécifier une ou plusieurs cibles, qui peuvent inclure une cible par défaut.

Chaque cible se compose d’une séquence d’une ou de plusieurs *tâches*. Chaque tâche est représentée par une classe .NET Framework qui contient une commande exécutable. Par exemple, la [tâche CL](/visualstudio/msbuild/cl-task) contient la commande [cl.exe](reference/compiling-a-c-cpp-program.md) .

Un *paramètre de tâche* est une propriété de la tâche de classe et représente généralement une option de ligne de commande de la commande exécutable. Par exemple, le `FavorSizeOrSpeed` paramètre de la `CL` tâche correspond aux options de compilateur **/OS** et **/OT** .

Les paramètres de tâche supplémentaires prennent en charge l’infrastructure MSBuild. Par exemple, le `Sources` paramètre de tâche spécifie un ensemble de tâches qui peuvent être consommées par d’autres tâches. Pour plus d’informations sur les tâches MSBuild, consultez [référence des tâches](/visualstudio/msbuild/msbuild-task-reference).

La plupart des tâches requièrent des entrées et des sorties, telles que des noms de fichiers, des chemins d’accès et des paramètres de chaîne, numériques ou booléens. Par exemple, une entrée courante est le nom d’un fichier source. cpp à compiler. Un paramètre d’entrée important est une chaîne qui spécifie la configuration et la plateforme de build, par exemple, « Debug \| Win32 ». Les entrées et les sorties sont spécifiées par un ou plusieurs éléments XML définis par l’utilisateur `Item` contenus dans un `ItemGroup` élément.

Un fichier projet peut également spécifier des *Propriétés* et des éléments définis par l’utilisateur `ItemDefinitionGroup` . Les propriétés et les éléments forment des paires nom/valeur qui peuvent être utilisées comme variables dans la Build. Le composant nom d’une paire définit une *macro* et le composant valeur déclare la valeur de la *macro*. Une macro de propriété est accessible à l’aide de la notation $ (*nom*), et une macro d’élément est accessible à l’aide de la notation%(*Name*).

D’autres éléments XML d’un fichier projet peuvent tester des macros, puis définir de manière conditionnelle la valeur d’une macro ou contrôler l’exécution de la Build. Les noms de macros et les chaînes littérales peuvent être concaténés pour générer des constructions telles qu’un chemin d’accès et un nom de fichier. Sur la ligne de commande, l’option **/Property** définit ou substitue une propriété de projet. Les éléments ne peuvent pas être référencés sur la ligne de commande.

Le système MSBuild peut exécuter de manière conditionnelle une cible avant ou après une autre cible. En outre, le système peut créer une cible selon que les fichiers utilisés par la cible sont plus récents que les fichiers qu’elle émet.

Pour plus d’informations sur MSBuild, consultez :

- [MSBuild](/visualstudio/msbuild/msbuild) Vue d’ensemble des concepts MSBuild.

- [Référence MSBuild](/visualstudio/msbuild/msbuild-reference) Informations de référence sur le système MSBuild.

- [Référence du schéma de fichier projet](/visualstudio/msbuild/msbuild-project-file-schema-reference) Répertorie les éléments de schéma XML MSBuild, ainsi que leurs attributs, ainsi que leurs éléments parents et enfants. Notez en particulier les éléments [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [target](/visualstudio/msbuild/target-element-msbuild)et [Task](/visualstudio/msbuild/task-element-msbuild) .

- [Référence de ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference) Décrit les arguments de ligne de commande et les options que vous pouvez utiliser avec msbuild.exe.

- [Référence de tâche](/visualstudio/msbuild/msbuild-task-reference) Décrit les tâches MSBuild. Notez en particulier ces tâches, qui sont spécifiques aux Visual C++ [: tâche BSCMAKE](/visualstudio/msbuild/bscmake-task), [tâche CL](/visualstudio/msbuild/cl-task), tâche [CPPClean,](/visualstudio/msbuild/cppclean-task), [tâche lib](/visualstudio/msbuild/lib-task), [tâche lien](/visualstudio/msbuild/link-task), tâche [MIDL](/visualstudio/msbuild/midl-task), [tâche MT](/visualstudio/msbuild/mt-task), [tâche RC](/visualstudio/msbuild/rc-task), tâche [setenv](/visualstudio/msbuild/setenv-task), [tâche VCMessage,](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>Dans cette section

|Terme|Définition|
|----------|----------------|
|[Procédure pas à pas : utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Montre comment créer un projet Visual Studio C++ à l’aide de **MSBuild**.|
|[Comment : utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Montre comment spécifier une action qui se produit à une étape particuler dans la génération : avant le démarrage de la génération ; avant le démarrage de l’étape de lien ; ou après la fin de la génération.|
|[Comment : ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Montre comment ajouter une étape définie par l’utilisateur à la séquence de génération.|
|[Comment : ajouter des outils de génération personnalisée à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Montre comment associer un outil de génération à un fichier particulier.|
|[Comment : intégrer des outils personnalisés dans les propriétés du projet](how-to-integrate-custom-tools-into-the-project-properties.md)|Montre comment ajouter des options pour un outil personnalisé aux propriétés du projet.|
|[Comment : modifier le Framework cible et l’ensemble d’outils de plateforme](how-to-modify-the-target-framework-and-platform-toolset.md)|Montre comment compiler un projet pour plusieurs infrastructures ou ensembles d’outils.|

## <a name="see-also"></a>Voir aussi

[Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)
