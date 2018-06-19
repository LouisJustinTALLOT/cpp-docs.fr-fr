---
title: 'Comment : ajouter des outils de génération personnalisée à des projets MSBuild | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3793e4223d00f219cc4f1d7b09e67453901bd6d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368328"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Comment : ajouter des outils de génération personnalisée à des projets MSBuild
Un outil de génération personnalisée est un outil de ligne de commande définis par l’utilisateur qui est associé à un fichier particulier.  
  
 Pour un fichier particulier, spécifiez dans le fichier projet (.vcxproj) de la ligne de commande à exécuter, aucune entrée supplémentaire ou des fichiers de sortie et un message à afficher. Si **MSBuild** détermine que vos fichiers de sortie sont obsolètes par rapport à vos fichiers d’entrée, il affiche le message et exécute l’outil de ligne de commande.  
  
 Pour spécifier quand l’outil de génération personnalisée s’exécute, utilisez un ou les deux le `CustomBuildBeforeTargets` et `CustomBuildAfterTargets` les éléments XML dans le fichier projet. Par exemple, vous pouvez spécifier que votre outil de génération personnalisée être exécutée le compilateur MIDL et le compilateur C/C++. Spécifiez le `CustomBuildBeforeTargets` élément pour exécuter l’outil avant l’exécution d’une cible particulière ; la `CustomBuildAfterTargets` pour exécuter l’outil après une cible particulière ; ou les deux éléments pour exécuter l’outil entre l’exécution de deux cibles. Si aucun élément n’est spécifié, votre outil de génération personnalisée s’exécute à son emplacement par défaut, c'est-à-dire avant le **MIDL** cible.  
  
 Étapes de génération personnalisée et des outils de génération personnalisée partagent les informations spécifiées dans le `CustomBuildBeforeTargets` et `CustomBuildAfterTargets` des éléments XML. Spécifiez ces cibles une fois dans votre fichier projet.  
  
### <a name="to-add-a-custom-build-tool"></a>Pour ajouter un outil de génération personnalisée  
  
1.  Ajouter un groupe d’éléments dans le fichier projet et ajouter un élément pour chaque fichier d’entrée. Spécifiez la commande, des entrées supplémentaires, des sorties et un message en tant que métadonnées de l’élément, comme indiqué ici. Cet exemple suppose qu’un fichier de « faq.txt » existe dans le même répertoire que votre projet.  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Pour définir où les outils de génération personnalisée seront exécutée dans la build  
  
1.  Ajoutez le groupe de propriétés suivant au fichier projet. Vous devez spécifier au moins l’une des cibles, mais vous pouvez omettre l’autre si vous souhaitez uniquement que votre étape de génération à exécuter avant (ou après) une cible particulière. Cet exemple exécute l’étape personnalisée après la compilation, mais avant la liaison.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Utilisation de MSBuild pour créer un projet Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Comment : utiliser des événements de Build dans des projets MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)