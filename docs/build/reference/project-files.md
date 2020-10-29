---
title: Exemple de fichier projet
ms.date: 08/19/2019
helpviewer_keywords:
- .vcxproj files
- C++ projects, project file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
ms.openlocfilehash: eef28961ab8c4d3a34a74999c7e0c69a4fc3fced
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924006"
---
# <a name="project-files"></a>Fichiers projet

Un fichier projet C++ dans Visual Studio est un fichier XML dont l’extension de nom de fichier est. vcxproj et qui contient les informations requises pour générer un projet C++. Notez que le fichier projet importe différents fichiers projet avec l’extension « . props » ou « . targets ». Ces fichiers contiennent des informations de build supplémentaires et peuvent eux-mêmes faire référence à d’autres fichiers « . props » ou « . targets ». Les macros contenues dans le chemin d’accès au fichier (par exemple `$(VCTargetsPath)`) dépendent de votre installation de Visual Studio. Pour plus d’informations sur ces macros et les fichiers « . props » et « . targets », consultez la [page de propriétés Répertoires VC + +](vcpp-directories-property-page.md), [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md) et les [macros courantes pour les commandes et propriétés de génération](common-macros-for-build-commands-and-properties.md).

## <a name="example"></a>Exemple

::: moniker range=">=msvc-160"

L’exemple de fichier. vcxproj suivant a été généré en choisissant **Assistant Windows Desktop** dans la boîte de dialogue **nouveau projet** . Pour traiter un fichier projet, utilisez l’outil msbuild.exe sur la ligne de commande, ou la commande **Générer** dans l’IDE. (Cet exemple ne peut pas être traité, car les fichiers sources et d’en-tête requis ne sont pas fournis.) Pour plus d’informations sur les éléments XML d’un fichier projet, consultez [Référence du schéma de fichier projet](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end

::: moniker range="<=msvc-150"

L’exemple de fichier .vcxproj suivant a été produit en spécifiant une **Application console Win32** dans la boîte de dialogue **Nouveau projet** . Pour traiter un fichier projet, utilisez l’outil msbuild.exe sur la ligne de commande, ou la commande **Générer** dans l’IDE. (Cet exemple ne peut pas être traité, car les fichiers sources et d’en-tête requis ne sont pas fournis.) Pour plus d’informations sur les éléments XML d’un fichier projet, consultez [Référence du schéma de fichier projet](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end

>[!NOTE]
> Pour les projets dans Visual Studio 2017 et versions antérieures, remplacez `pch.h` par `stdafx.h` et par `pch.cpp` `stdafx.cpp` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup Label="ProjectConfigurations">
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <PropertyGroup Label="Globals">
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>
    <Keyword>Win32Proj</Keyword>
    <RootNamespace>SomeProjName</RootNamespace>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <WholeProgramOptimization>true</WholeProgramOptimization>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings">
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <LinkIncremental>true</LinkIncremental>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <LinkIncremental>false</LinkIncremental>
  </PropertyGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <ClCompile>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <WarningLevel>Level3</WarningLevel>
      <MinimalRebuild>true</MinimalRebuild>
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>
      <Optimization>Disabled</Optimization>
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
    </Link>
  </ItemDefinitionGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <ClCompile>
      <WarningLevel>Level3</WarningLevel>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>
      <Optimization>MaxSpeed</Optimization>
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
      <FunctionLevelLinking>true</FunctionLevelLinking>
      <IntrinsicFunctions>true</IntrinsicFunctions>
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
      <EnableCOMDATFolding>true</EnableCOMDATFolding>
      <OptimizeReferences>true</OptimizeReferences>
    </Link>
  </ItemDefinitionGroup>
  <ItemGroup>
    <None Include="ReadMe.txt" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="pch.h" />
    <ClInclude Include="targetver.h" />
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="SomeProjName.cpp" />
    <ClCompile Include="pch.cpp">
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>
    </ClCompile>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets">
  </ImportGroup>
</Project>
```

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)
