---
title: fichiers. vcxproj et caractères génériques
description: Comment les fichiers System. vcxproj du projet MSBuild natif C++ gèrent les caractères génériques.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 23d36a63f328e14cca59d1d57838173b4dcb0954
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662881"
---
# <a name="vcxproj-files-and-wildcards"></a>`.vcxproj` fichiers et caractères génériques

L’IDE de Visual Studio ne prend pas en charge certaines constructions dans les éléments de projet des *`.vcxproj`* fichiers. Ces constructions non prises en charge incluent des caractères génériques, des listes délimitées par des points-virgules ou des macros MSBuild qui s’étendent à plusieurs fichiers. Le `.vcxproj` système de projet pour les builds C++ est plus restrictif que MSBuild. Chaque élément de projet doit avoir son propre élément MSBuild. Pour plus d’informations sur le `.vcxproj` format de fichier, consultez [ `.vcxproj` et `.props` structure de fichiers](vcxproj-file-structure.md).

Ces exemples de construction ne sont pas pris en charge par l’IDE :

```xml
<ItemGroup>
  <None Include="*.txt">
  <ClCompile Include="a.cpp;b.cpp"/>
  <ClCompile Include="@(SomeItems)" />
</ItemGroup>
```

Si un `.vcxproj` fichier projet qui comprend ces constructions est chargé dans l’IDE, le projet peut sembler fonctionner dans un premier temps. Toutefois, les problèmes sont susceptibles de se faire dès que le projet est modifié par Visual Studio, puis enregistrés sur le disque. Vous pouvez rencontrer des blocages aléatoires et un comportement non défini.

Dans Visual Studio 2019 version 16,7, quand Visual Studio charge un `.vcxproj` fichier projet, il détecte automatiquement les entrées non prises en charge dans les éléments de projet. Des avertissements s’affichent dans la fenêtre sortie pendant le chargement de la solution.

Visual Studio 2019 version 16,7 ajoute également la prise en charge des projets en lecture seule. La prise en charge en lecture seule permet à l’IDE d’utiliser des projets créés manuellement qui n’ont pas les limitations supplémentaires des projets modifiables par l’IDE.

Si vous disposez `.vcxproj` d’un fichier qui utilise une ou plusieurs des constructions non prises en charge, vous pouvez le faire charger sans avertissements dans l’IDE en utilisant l’une des options suivantes :

- Répertorier tous les éléments explicitement
- Marquer votre projet en lecture seule
- Déplacer des éléments génériques vers un corps cible

## <a name="list-all-items-explicitly"></a>Répertorier tous les éléments explicitement

Actuellement, il n’existe aucun moyen d’afficher les éléments de développement de caractères génériques dans la fenêtre de Explorateur de solutions dans un projet qui n’est pas en lecture seule. Explorateur de solutions s’attend à ce que les projets répertorient tous les éléments explicitement.

Pour que `.vcxproj` les projets développent automatiquement des caractères génériques dans Visual Studio 2019 version 16,7 ou ultérieure, affectez à la propriété la valeur `ReplaceWildcardsInProjectItems` `true` . Nous vous recommandons de créer un *`Directory.Build.props`* fichier dans un répertoire racine et d’utiliser ce contenu :

```xml
<Project>
  <PropertyGroup>
    <ReplaceWildcardsInProjectItems>true</ReplaceWildcardsInProjectItems>
  </PropertyGroup>
</Project>
```

## <a name="mark-your-project-as-read-only"></a>Marquer votre projet en lecture seule

Dans Visual Studio 2019 version 16,7 et versions ultérieures, vous pouvez marquer des projets en *lecture seule*. Pour marquer votre projet en lecture seule, ajoutez la propriété suivante à votre *`.vcxproj`* fichier ou à n’importe quel fichier importé :

```xml
<PropertyGroup>
    <ReadOnlyProject>true</ReadOnlyProject>
</PropertyGroup>
```

Le `<ReadOnlyProject>` paramètre empêche Visual Studio de modifier et d’enregistrer le projet, de sorte que vous pouvez utiliser toutes les constructions MSBuild qu’il contient, y compris les caractères génériques.

Il est important de savoir que le cache de projet n’est pas disponible si Visual Studio détecte les caractères génériques dans les éléments de projet dans le *`.vcxproj`* fichier ou dans l’une de ses importations. Les temps de chargement de la solution dans l’IDE sont beaucoup plus longs si vous avez un grand nombre de projets qui utilisent des caractères génériques.

## <a name="move-wildcard-items-to-a-target-body"></a>Déplacer des éléments génériques vers un corps cible

Vous pouvez utiliser des caractères génériques pour collecter des ressources, ajouter des sources générées, et ainsi de suite. Si vous n’en avez pas besoin dans la fenêtre de Explorateur de solutions, vous pouvez utiliser cette procédure à la place :

1. Modifiez le nom du groupe d’éléments pour ajouter des caractères génériques. Par exemple, au lieu de :

   ```xml
   <Image Include="*.bmp" />
   <ClCompile Include="*.cpp" />
   ```

   Remplacez-le par :

   ```xml
   <_WildCardImage Include="*.bmp" />
   <_WildCardClCompile Include="*.cpp" />
   ```

1. Ajoutez ce contenu à votre  *`.vcxproj`* fichier.Ou ajoutez-le à un *`Directory.Build.targets`* fichier dans un répertoire racine pour affecter tous les projets sous cette racine :

   ```xml
   <Target Name="AddWildCardItems"
       AfterTargets="BuildGenerateSources">
     <ItemGroup>
       <Image Include="@(_WildCardImage)" />
       <ClCompile Include="@(_WildCardClCompile)" />
     </ItemGroup>
   </Target>
   ```

   Cette modification permet à la build de voir les éléments tels qu’ils sont définis dans le  *`.vcxproj`* fichier. Toutefois, ils ne sont pas visibles dans la fenêtre Explorateur de solutions et ne provoquent pas de problèmes dans l’IDE.

1. Pour afficher la correction IntelliSense correcte des  `_WildCardClCompile`   éléments lorsque vous ouvrez ces fichiers dans l’éditeur, ajoutez le contenu suivant :

   ```xml
   <PropertyGroup>
     <ComputeCompileInputsTargets>
       AddWildCardItems
       $(ComputeCompileInputsTargets)
     </ComputeCompileInputsTargets>
   </PropertyGroup>
   ```

En effet, vous pouvez utiliser des caractères génériques pour tous les éléments à l’intérieur d’un corps cible. Vous pouvez également utiliser des caractères génériques dans un  `ItemGroup`   qui n’est pas défini en tant qu’élément de projet par un [`ProjectSchemaDefinition`](https://devblogs.microsoft.com/cppblog/vc-MSBuild-extensibility-example/) .

> [!NOTE]
> Si vous déplacez des caractères génériques d’un *`.vcxproj`* fichier vers un fichier importé, ceux-ci ne sont pas visibles dans la fenêtre de Explorateur de solutions. Cette modification permet également à votre projet de se charger dans l’IDE sans modification. Toutefois, cette approche n’est pas recommandée, car elle désactive le cache de projet.

## <a name="see-also"></a>Voir aussi

[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)<br/>
[Fichiers XML de page de propriétés](property-page-xml-files.md)
