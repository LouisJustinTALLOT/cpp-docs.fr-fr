---
description: En savoir plus sur les macros courantes pour les commandes et les propriétés MSBuild
title: Macros courantes pour les commandes et les propriétés MSBuild
ms.date: 08/02/2019
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 3911e3285ca09fefce51f0522690943b1f8b2c27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179107"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Macros courantes pour les commandes et les propriétés MSBuild

Selon vos options d’installation, Visual Studio peut mettre à votre disposition des centaines de macros dans un projet Visual Studio (basé sur MSBuild). Ils correspondent aux propriétés MSBuild définies par défaut, ou dans les fichiers. props ou. targets, ou dans les paramètres de votre projet. Vous pouvez utiliser ces macros partout dans la boîte de dialogue **Pages de propriétés** d’un projet où les chaînes sont acceptées. Ces macros ne respectent pas la casse.

## <a name="view-the-current-properties-and-macros"></a>Voir les propriétés et macros actuelles

Pour afficher toutes les macros actuellement disponibles, dans la boîte de dialogue **pages de propriétés** , sous **Répertoires VC + +**, choisissez la flèche déroulante à la fin d’une ligne de propriété. Cliquez sur **modifier** , puis dans la boîte de dialogue Modifier, choisissez le bouton **macros** . L’ensemble actuel de propriétés et de macros accessible à Visual Studio est répertorié avec la valeur actuelle de chacune d’entre elles. Pour plus d’informations, consultez la section **spécification des valeurs User-Defined** de la [page de référence des pages de propriétés du projet C++](property-pages-visual-cpp.md).

![Bouton macros VC + +](../media/vcppdir_libdir_macros.png "Menu Macros")

## <a name="list-of-common-macros"></a>Liste des macros courantes

Ce tableau décrit un sous-ensemble couramment utilisé des macros disponibles. Il y en a beaucoup plus non répertorié ici. Accédez à la boîte de dialogue **macros** pour afficher toutes les propriétés et leurs valeurs actuelles dans votre projet. Pour plus d’informations sur la création et l’utilisation des définitions de propriété MSBuild sous forme de macros dans des fichiers .vcxproj .props et .targets, consultez [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Description|
|-----------|-----------------|
|**$ (Configuration)**|Nom de la configuration de projet actuelle, par exemple « Debug ».|
|**$(DevEnvDir)**|Répertoire d’installation de Visual Studio (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(FrameworkDir)**|Le répertoire où le .NET Framework a été installé.|
|**$(FrameworkSDKDir)**|Le répertoire où vous avez installé le .NET Framework. Le .NET Framework peut avoir été installé dans le cadre de Visual Studio ou bien séparément.|
|**$ (FrameworkVersion)**|La version du .NET Framework utilisée par Visual Studio. Combiné avec **$(FrameworkDir)**, le chemin complet de la version du .NET Framework utilisé par Visual Studio.|
|**$(FxCopDir)**|Le chemin du fichier fxcop.cmd. Le fichier FxCop. cmd n’est pas installé avec toutes les éditions de Visual Studio.|
|**$(IntDir)**|Chemin du répertoire spécifié pour les fichiers intermédiaires. S’il s’agit d’un chemin d’accès relatif, les fichiers intermédiaires sont placés dans ce chemin d’accès ajouté au répertoire du projet. Ce chemin doit se terminer par une barre oblique. Il correspond à la valeur de la propriété **Intermediate Directory** . N’utilisez pas **$ (OutDir)** pour définir cette propriété.|
|**$ (OutDir)**|Chemin du répertoire des fichiers de sortie. S’il s’agit d’un chemin d’accès relatif, les fichiers de sortie sont placés dans ce chemin d’accès ajouté au répertoire du projet. Ce chemin doit se terminer par une barre oblique. Il correspond à la valeur de la propriété du **Répertoire de sortie** . N’utilisez pas **$ (IntDir)** pour définir cette propriété.|
|**$ (Plateforme)**|Nom de la plateforme de projet actuelle, par exemple, « Win32 ».|
|**$ (PlatformShortName)**|Nom abrégé de l’architecture actuelle, par exemple « x86 » ou « x64 ».|
|**$(ProjectDir)**|Répertoire du projet (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(ProjectExt)**|L’extension de fichier du projet. Elle inclut le point (« . ») avant l’extension de fichier.|
|**$(ProjectFileName)**|Le nom de fichier du projet (défini comme étant nom de base + extension de fichier).|
|**$ (ProjectName)**|Le nom de base du projet.|
|**$(ProjectPath)**|Le nom du chemin absolu du projet (défini comme étant lecteur + chemin + nom de base + extension de fichier).|
|**$ (PublishDir)**|Emplacement de sortie de la cible de publication ; comprend la barre oblique inverse de fin' \\ '. La valeur par défaut est le dossier **$ (OutDir) \\ app. Publish** .|
|**$(RemoteMachine)**|Définit sur la valeur de la propriété **Remote Machine** sur la page des propriétés du débogage. Pour plus d’informations, consultez [Modification des paramètres du projet pour une configuration Debug C ou C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$ (RootNameSpace)**|L’espace de noms, s’il y en a un, contenant l’application.|
|**$(SolutionDir)**|Répertoire de la solution (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ». Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionExt)**|L’extension de fichier de la solution. Elle inclut le point (« . ») avant l’extension de fichier. Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionFileName)**|Le nom de fichier de la solution (défini comme étant nom de base + extension de fichier). Défini uniquement quand une solution est générée dans l’IDE.|
|**$ (SolutionName)**|Le nom de base de la solution. Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionPath)**|Le nom du chemin absolu de la solution (défini comme étant lecteur + chemin + nom de base + extension de fichier). Défini uniquement quand une solution est générée dans l’IDE.|
|**$(TargetDir)**|Répertoire du fichier de sortie principal pour la build (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(TargetExt)**|L’extension de fichier du fichier de sortie principal pour la build. Elle inclut le point (« . ») avant l’extension de fichier.|
|**$(TargetFileName)**|Le nom de fichier du fichier de sortie principal pour la build (défini comme étant nom de base + extension de fichier).|
|**$ (TargetName)**|Le nom de base du fichier de sortie principal pour la build.|
|**$(TargetPath)**|Le nom du chemin absolu du fichier de sortie principal pour la build (défini comme étant lecteur + chemin + nom de base + extension de fichier).|
|**$(VCInstallDir)**|Répertoire qui comprend le contenu C++ de votre installation de Visual Studio. Cette propriété contient la version de l’ensemble d’outils Microsoft C++ (MSVC) ciblé, qui peut être différente de l’hôte Visual Studio. Par exemple, lors de la génération avec `$(PlatformToolset) = v140` , **$ (VCInstallDir)** contient le chemin d’accès à l’installation de Visual Studio 2015.|
|**$(VSInstallDir)**|Le répertoire où vous avez installé Visual Studio. Cette propriété contient la version de l’ensemble d’outils Visual Studio ciblé, qui peut être différente de celle du Visual Studio hôte. Par exemple, lors d’une génération avec `$(PlatformToolset) = v110`, **$(VSInstallDir)** contient le chemin de l’installation de Visual Studio 2012.|
|**$(WebDeployPath)**|Le chemin relatif à partir de la racine du déploiement auquel les sorties du projet appartiennent.|
|**$(WebDeployRoot)**|Chemin d’accès absolu à l’emplacement de **\<localhost>** . Par exemple, c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Macros obsolètes

Le système de build pour C++ a considérablement changé entre Visual Studio 2008 et Visual Studio 2010. Plusieurs macros utilisées dans les types de projet antérieurs ont été remplacées par de nouvelles macros. Ces macros ne sont plus utilisées ou ont été remplacées par une ou plusieurs propriétés ou valeurs de [macro de métadonnées d’élément](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_nom_**)**) équivalentes. Les macros marquées comme « migrées » peuvent être mises à jour par l’outil de migration de projet. Si le projet contenant la macro migre depuis Visual Studio 2008 ou une version antérieure vers Visual Studio 2010, Visual Studio convertit la macro en macro actuelle équivalente. Les versions ultérieures de Visual Studio ne peuvent pas convertir des projets Visual Studio 2008 et antérieur en nouveau type de projet. Vous devez convertir ces projets en deux temps ; tout d’abord, convertissez-les en Visual Studio 2010, puis convertissez le résultat en version récente de Visual Studio. Pour plus d’informations, consultez [Vue d’ensemble des problèmes de mise à niveau potentiels](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Description|
|-----------|-----------------|
|**$ (InputDir)**|(Migré.) Répertoire du fichier d’entrée (sous la forme lecteur + chemin d’accès); comprend la barre oblique inverse de fin' \\ '. Si le projet est l’entrée, cette macro est équivalente à **$(ProjectDir)**.|
|**$(InputExt)**|(Migré.) Extension de fichier du fichier d’entrée. Elle inclut le point (« . ») avant l’extension de fichier. Si le projet est l’entrée, cette macro est équivalente à **$(ProjectExt)**. Pour les fichiers sources, il s’agit de **%(Extension)**.|
|**$ (InputFileName)**|(Migré.) Nom de fichier du fichier d’entrée (défini comme nom de base + extension de fichier). Si le projet est l’entrée, cette macro est équivalente à **$(ProjectFileName)**. Pour les fichiers sources, il s’agit de **%(Identity)**.|
|**$ (InputName)**|(Migré.) Nom de base du fichier d’entrée. Si le projet est l’entrée, cette macro est équivalente à **$(ProjectName)**. Pour les fichiers sources, il s’agit de **%(Filename)**.|
|**$(InputPath)**|(Migré.) Nom de chemin d’accès absolu du fichier d’entrée (défini en tant que lecteur + chemin d’accès + nom de base + extension de fichier). Si le projet est l’entrée, cette macro est équivalente à **$(ProjectPath)**. Pour les fichiers sources, il s’agit de **%(FullPath)**.|
|**$ (ParentName)**|Nom de l’élément contenant cet élément de projet. Il s’agira du nom du dossier parent ou du nom du projet.|
|**$(SafeInputName)**|Le nom du fichier sous forme de nom de classe valide, moins l’extension de fichier. Cette propriété n’a pas d’équivalent exact.|
|**$(SafeParentName)**|Le nom du parent immédiat dans un format de nom valide. Par exemple, une forme est le parent d’un fichier .resx. Cette propriété n’a pas d’équivalent exact.|
|**$(SafeRootNamespace)**|Le nom de l’espace de noms où les Assistants Projet ajouteront le code. Cet espace de noms contiendra seulement des caractères qui sont autorisés dans un identificateur C++ valide. Cette propriété n’a pas d’équivalent exact.|

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](../creating-and-managing-visual-cpp-projects.md)\
[Guide de Portage et de mise à niveau de Visual C++](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[Vue d’ensemble des problèmes de mise à niveau potentiels](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
