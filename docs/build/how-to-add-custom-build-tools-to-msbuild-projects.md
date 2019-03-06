---
title: 'Procédure : Ajouter des outils de génération personnalisée à des projets MSBuild'
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: d07c8de3405791e94193368e921c0f594845a418
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413847"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Procédure : Ajouter des outils de génération personnalisée à des projets MSBuild

Un outil de génération personnalisée est un outil de ligne de commande, défini par l’utilisateur qui est associé à un fichier particulier.

Pour un fichier particulier, spécifiez dans le fichier projet (.vcxproj) sur la ligne de commande à exécuter, toute entrée supplémentaire ou des fichiers de sortie et un message à afficher. Si **MSBuild** détermine que vos fichiers de sortie sont obsolètes en ce qui concerne vos fichiers d’entrée, il affiche le message et exécute l’outil de ligne de commande.

Pour spécifier quand l’outil de génération personnalisée s’exécute, utilisez une ou les deux le `CustomBuildBeforeTargets` et `CustomBuildAfterTargets` les éléments XML dans le fichier projet. Par exemple, vous pouvez spécifier que votre outil de génération personnalisée exécutée le compilateur MIDL et le compilateur C/C++. Spécifiez le `CustomBuildBeforeTargets` élément pour exécuter l’outil avant l’exécution d’une cible particulière ; le `CustomBuildAfterTargets` élément à exécuter l’outil après une cible particulière ; ou les deux éléments pour exécuter l’outil entre l’exécution de deux cibles. Si aucun élément n’est spécifié, votre outil de génération personnalisée s’exécute à son emplacement par défaut, c'est-à-dire avant le **MIDL** cible.

Étapes de génération personnalisée et des outils de génération personnalisée partagent les informations spécifiées dans le `CustomBuildBeforeTargets` et `CustomBuildAfterTargets` éléments XML. Spécifiez ces cibles une seule fois dans votre fichier projet.

### <a name="to-add-a-custom-build-tool"></a>Pour ajouter un outil de génération personnalisée

1. Ajouter un groupe d’éléments dans le fichier projet et ajouter un élément pour chaque fichier d’entrée. Spécifiez la commande, des entrées supplémentaires, des sorties et un message en tant que métadonnées d’élément, comme indiqué ici. Cet exemple suppose qu’un fichier de « faq.txt » existe dans le même répertoire que votre projet.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Pour définir où les outils de génération personnalisée seront exécute dans la build

1. Ajoutez le groupe de propriétés suivant au fichier projet. Vous devez spécifier au moins une des cibles, mais vous pouvez omettre l’autre si vous êtes uniquement intéressé par une étape de votre build à exécuter avant (ou après) une cible particulière. Cet exemple exécute l’étape personnalisée après la compilation, mais avant la liaison.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Guide pratique pour utiliser des événements de génération dans des projets MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)
