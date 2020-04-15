---
title: Vcxproj.filtre les fichiers
ms.date: 09/25/2019
description: Utilisez des fichiers de filtres dans les projets Visual Studio CMD pour définir des dossiers logiques personnalisés pour les fichiers dans Solution Explorer
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335930"
---
# <a name="vcxprojfilters-files"></a>vcxproj.filtre les fichiers

Le fichier de\* *filtres* (.vcxproj.filters) est un fichier XML dans le format MSBuild qui est situé dans le dossier de projet racine. Il précise quels types de fichiers entrent dans quel dossier logique dans **Solution Explorer**. Dans l’illustration suivante, les fichiers *.cpp* sont sous le nœud **Source Files.** les fichiers *.h* sont sous le nœud **Header Files,** et *.ico* et *.rc* fichiers sont sous **fichiers de ressources**. Ce placement est contrôlé par le fichier des filtres.

![Dossiers logiques dans Solution Explorer](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Création d’un fichier de filtres personnalisés

Visual Studio crée ce fichier automatiquement. Pour les applications de bureau, les dossiers logiques prédéfinis (filtres) sont : **Fichiers Source**, **Fichiers d’en-tête** et **fichiers de ressources**. D’autres types de projets tels que UWP peuvent avoir un ensemble différent de dossiers par défaut. Visual Studio attribue automatiquement des types de fichiers connus à chaque dossier. Si vous souhaitez créer un filtre avec un nom personnalisé ou un filtre qui contient des types de fichiers personnalisés, vous pouvez créer votre propre fichier de filtres dans le dossier racine du projet, ou sous un filtre existant. (**Les références** et les **dépendances externes** sont des dossiers spéciaux qui ne participent pas au filtrage.)

## <a name="example"></a>Exemple

L’exemple suivant montre le fichier de filtres pour l’exemple s’afficher précédemment. Il a une hiérarchie plate; en d’autres termes, il n’y a pas de dossiers logiques imbriqués. Le nœud `UniqueIdentifier` est facultatif. Il permet aux interfaces d’automatisation Visual Studio de trouver le filtre. `Extensions`est également facultatif. Lorsqu’un nouveau fichier est ajouté à un projet, il est ajouté au filtre le plus haut avec une extension de fichier correspondante. Pour ajouter un fichier à un filtre spécifique, cliquez à droite sur le filtre et choisissez **Ajouter un nouvel élément**.

Le `ItemGroup` qui `ClInclude` contient les nœuds est créé lorsque le projet est lancé. Si vous génévez vos propres fichiers vcxproj, assurez-vous que tous les éléments du projet ont également une entrée dans le fichier des filtres. Les valeurs `ClInclude` d’un nœud remplacent le filtrage par défaut en fonction des extensions de fichiers. Lorsque vous utilisez Visual Studio pour ajouter un nouvel élément au projet, l’IDE ajoutera une entrée de fichier individuelle dans le fichier des filtres. Le filtre n’est pas automatiquement réaffecté si vous modifiez l’extension du fichier.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

Pour créer des dossiers logiques imbriqués, déclarez tous les nœuds dans les filtres `ItemGroup` comme indiqué ci-dessous. Chaque nœud d’enfant doit déclarer le chemin logique complet vers le parent le plus haut. Dans l’exemple suivant, un vide `ParentFilter` doit être déclaré parce qu’il est référencé dans les nœuds ultérieurs.

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```
