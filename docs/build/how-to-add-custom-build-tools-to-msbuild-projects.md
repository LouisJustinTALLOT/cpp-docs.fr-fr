---
description: 'En savoir plus sur : Comment : ajouter des outils de génération personnalisée à des projets MSBuild'
title: 'Comment : ajouter des outils de génération personnalisée à des projets MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 66ec4a488fd2a089f09ac775d1150300ff662ff2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162818"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Comment : ajouter des outils de génération personnalisée à des projets MSBuild

Un outil de génération personnalisée est un outil de ligne de commande défini par l’utilisateur qui est associé à un fichier particulier.

Pour un fichier particulier, spécifiez dans le fichier projet (. vcxproj) la ligne de commande à exécuter, tous les fichiers d’entrée ou de sortie supplémentaires et un message à afficher. Si **MSBuild** détermine que vos fichiers de sortie sont obsolètes par rapport à vos fichiers d’entrée, il affiche le message et exécute l’outil en ligne de commande.

Pour spécifier à quel moment l’outil de génération personnalisée s’exécute, utilisez l’un des éléments XML, ou les deux, `CustomBuildBeforeTargets` `CustomBuildAfterTargets` dans le fichier projet. Par exemple, vous pouvez spécifier que votre outil de génération personnalisée s’exécute après le compilateur MIDL et avant le compilateur C/C++. Spécifiez l' `CustomBuildBeforeTargets` élément pour exécuter l’outil avant l’exécution d’une cible particulière ; l' `CustomBuildAfterTargets` élément pour exécuter l’outil après une cible particulière, ou les deux éléments pour exécuter l’outil entre l’exécution de deux cibles. Si aucun élément n’est spécifié, votre outil de génération personnalisée s’exécute à son emplacement par défaut, qui est antérieur à la cible **MIDL** .

Les étapes de génération personnalisée et les outils de génération personnalisés partagent les informations spécifiées dans les `CustomBuildBeforeTargets` `CustomBuildAfterTargets` éléments et XML. Spécifiez ces cibles une fois dans votre fichier projet.

### <a name="to-add-a-custom-build-tool"></a>Pour ajouter un outil de génération personnalisée

1. Ajoutez un groupe d’éléments au fichier projet et ajoutez un élément pour chaque fichier d’entrée. Spécifiez la commande, les entrées supplémentaires, les sorties et un message en tant que métadonnées d’élément, comme indiqué ici. Cet exemple suppose qu’un fichier « faq.txt » existe dans le même répertoire que votre projet.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Pour définir l’emplacement d’exécution des outils de génération personnalisée

1. Ajoutez le groupe de propriétés suivant au fichier projet. Vous devez spécifier au moins l’une des cibles, mais vous pouvez omettre l’autre si vous souhaitez seulement que votre étape de génération s’exécute avant (ou après) une cible particulière. Cet exemple exécute l’étape personnalisée après la compilation mais avant la liaison.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Comment : utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Comment : ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
