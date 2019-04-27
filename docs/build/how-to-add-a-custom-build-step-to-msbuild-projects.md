---
title: 'Procédure : Ajoutez une étape de génération personnalisée à des projets MSBuild'
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 4c64c6875d82000d6a0ac880b103b5e220015cb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188923"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Procédure : Ajoutez une étape de génération personnalisée à des projets MSBuild

Une étape de génération personnalisée est une étape définie par l’utilisateur dans une build. Une étape de génération personnalisée se comporte comme n’importe quel autre *outil de commande* étape, telles que l’étape d’outil de compilation ou de liaison standard.

Spécifiez une étape de génération personnalisée dans le fichier projet (.vcxproj). L’étape peut spécifier une ligne de commande à exécuter, toute entrée supplémentaire ou des fichiers de sortie et un message à afficher. Si **MSBuild** détermine que vos fichiers de sortie sont obsolètes par rapport à vos fichiers d’entrée, il affiche le message et exécute la commande.

Pour spécifier l’emplacement de la génération personnalisée étape dans la séquence des cibles de génération, utilisez une ou les deux le `CustomBuildAfterTargets` et `CustomBuildBeforeTargets` les éléments XML dans le fichier projet. Par exemple, vous pouvez spécifier que l’étape de génération personnalisée s’exécute après la cible du lien outil et avant la cible de l’outil manifeste. Le jeu réel de cibles disponibles dépend de votre build particulière.

Spécifiez le `CustomBuildBeforeTargets` élément pour exécuter l’étape de génération personnalisée avant l’exécution d’une cible particulière, le `CustomBuildAfterTargets` pour exécuter l’étape après l’exécution d’une cible particulière, ou les deux éléments pour exécuter l’étape entre deux cibles adjacentes. Si aucun élément n’est spécifié, votre outil de génération personnalisée s’exécute à son emplacement par défaut, c'est-à-dire après le **lien** cible.

Étapes de génération personnalisée et des outils de génération personnalisée partagent les informations spécifiées dans le `CustomBuildBeforeTargets` et `CustomBuildAfterTargets` éléments XML. Par conséquent, spécifiez ces cibles qu’une seule fois dans votre fichier projet.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Pour définir ce qui est exécuté par l’étape de génération personnalisée

1. Ajouter un groupe de propriétés au fichier projet. Dans ce groupe de propriétés, spécifiez la commande, ses entrées et sorties et un message, comme indiqué dans l’exemple suivant. Cet exemple crée un fichier .cab à partir du fichier main.cpp que vous avez créé dans [procédure pas à pas : Utilisation de MSBuild pour créer un projet Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Pour définir où s’exécute l’étape de génération personnalisée dans la build

1. Ajoutez le groupe de propriétés suivant au fichier projet. Vous pouvez spécifier les deux cibles, ou vous pouvez omettre un si vous souhaitez simplement l’étape personnalisée à exécuter avant ou après une cible particulière. Cet exemple indique à **MSBuild** pour effectuer l’étape personnalisée après l’étape de compilation, mais avant l’étape de liaison.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Guide pratique pour utiliser des événements de génération dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Guide pratique pour ajouter des outils de génération personnalisée à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
