---
title: 'Comment : ajouter une étape de génération personnalisée à des projets MSBuild'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444921"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Comment : ajouter une étape de génération personnalisée à des projets MSBuild

Une étape de génération personnalisée est une étape définie par l’utilisateur dans une génération. Une étape de génération personnalisée se comporte comme toute autre étape d' *outil de commande* , telle que l’étape de compilation ou d’outil de liaison standard.

Spécifiez une étape de génération personnalisée dans le fichier projet (. vcxproj). L’étape peut spécifier une ligne de commande à exécuter, tous les fichiers d’entrée ou de sortie supplémentaires et un message à afficher. Si **MSBuild** détermine que vos fichiers de sortie sont obsolètes par rapport à vos fichiers d’entrée, il affiche le message et exécute la commande.

Pour spécifier l’emplacement de l’étape de génération personnalisée dans l’ordre des cibles de génération, utilisez l’un des `CustomBuildAfterTargets` éléments `CustomBuildBeforeTargets` XML, ou les deux, dans le fichier projet. Par exemple, vous pouvez spécifier que l’étape de génération personnalisée s’exécute après l’outil de liaison cible et avant la cible de l’outil manifeste. L’ensemble réel des cibles disponibles dépend de votre build particulière.

Spécifiez `CustomBuildBeforeTargets` l’élément pour exécuter l’étape de génération personnalisée avant l’exécution d’une `CustomBuildAfterTargets` cible particulière, l’élément pour exécuter l’étape après l’exécution d’une cible particulière, ou les deux éléments pour exécuter l’étape entre deux cibles adjacentes. Si aucun élément n’est spécifié, votre outil de génération personnalisée s’exécute à son emplacement par défaut, qui est après la cible du **lien** .

Les étapes de génération personnalisée et les outils de génération personnalisés partagent les `CustomBuildBeforeTargets` informations `CustomBuildAfterTargets` spécifiées dans les éléments et XML. Par conséquent, spécifiez ces cibles une seule fois dans votre fichier projet.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Pour définir ce qui est exécuté par l’étape de génération personnalisée

1. Ajoutez un groupe de propriétés au fichier projet. Dans ce groupe de propriétés, spécifiez la commande, ses entrées et sorties, ainsi qu’un message, comme indiqué dans l’exemple suivant. Cet exemple crée un fichier. cab à partir du fichier main. cpp que vous avez créé dans [procédure pas à pas : utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Pour définir l’emplacement d’exécution de l’étape de génération personnalisée

1. Ajoutez le groupe de propriétés suivant au fichier projet. Vous pouvez spécifier les deux cibles ou omettre l’une d’elles si vous souhaitez que l’étape personnalisée soit exécutée avant ou après une cible particulière. Cet exemple indique à **MSBuild** d’exécuter l’étape personnalisée après l’étape de compilation, mais avant l’étape de liaison.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Comment : utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Guide pratique pour ajouter des outils de génération personnalisés à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
