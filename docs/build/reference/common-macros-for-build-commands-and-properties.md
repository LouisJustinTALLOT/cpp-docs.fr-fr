---
title: Macros courantes pour les propriétés et les commandes de build
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
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
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 669114691bc89c1e8136e07a949be57cda3d71b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825439"
---
# <a name="common-macros-for-build-commands-and-properties"></a>Macros courantes pour les propriétés et les commandes de build

Selon vos options d’installation, Visual Studio peut proposer des centaines de macros. Celles-ci correspondent aux propriétés MSBuild définies par défaut, à des fichiers .props ou .targets, ou aux paramètres de votre projet. Vous pouvez utiliser ces macros partout dans la boîte de dialogue **Pages de propriétés** d’un projet où les chaînes sont acceptées. Ces macros ne respectent pas la casse.

## <a name="view-the-current-properties-and-macros"></a>Voir les propriétés et macros actuelles

Pour afficher les macros actuellement disponibles, dans une page de propriétés de la boîte de dialogue **Pages de propriétés**, choisissez la flèche déroulante à la fin d’une ligne de propriété. Si l’option **Modifier** est disponible, choisissez-la, puis dans la boîte de dialogue de modification, choisissez le bouton **Macros**. L’ensemble actuel de propriétés et de macros accessible à Visual Studio est répertorié avec la valeur actuelle de chacune d’entre elles. Pour plus d’informations, consultez le **Specifying User-Defined valeurs** section de [référence de page de propriété de projet C++](property-pages-visual-cpp.md).

## <a name="list-of-common-macros"></a>Liste des macros courantes

Le tableau suivant décrit une partie des macros disponibles couramment utilisées. Cette liste est loin d’être exhaustive. Pour plus d’informations sur la création et l’utilisation des définitions de propriété MSBuild sous forme de macros dans des fichiers .vcxproj .props et .targets, consultez [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Description|
|-----------|-----------------|
|**$(Configuration)**|Nom de la configuration de projet actuelle, par exemple « Debug ».|
|**$(DevEnvDir)**|Répertoire d’installation de Visual Studio (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(FrameworkDir)**|Le répertoire où le .NET Framework a été installé.|
|**$(FrameworkSDKDir)**|Le répertoire où vous avez installé le .NET Framework. Le .NET Framework peut avoir été installé dans le cadre de Visual Studio ou bien séparément.|
|**$(FrameworkVersion)**|La version du .NET Framework utilisée par Visual Studio. Combiné avec **$(FrameworkDir)**, le chemin complet de la version du .NET Framework utilisé par Visual Studio.|
|**$(FxCopDir)**|Le chemin du fichier fxcop.cmd. Le fichier fxcop.cmd n’est pas installé avec toutes les éditions de Visual C++.|
|**$(IntDir)**|Chemin du répertoire spécifié pour les fichiers intermédiaires. S’il s’agit d’un chemin relatif, les fichiers intermédiaires sont placés dans ce chemin ajouté au répertoire du projet. Ce chemin doit se terminer par une barre oblique. Ceci se résout en la valeur de la propriété **Intermediate Directory** . N’utilisez pas **$(OutDir)** pour définir cette propriété.|
|**$(OutDir)**|Chemin du répertoire des fichiers de sortie. S’il s’agit d’un chemin relatif, les fichiers de sortie sont placés dans ce chemin ajouté au répertoire du projet. Ce chemin doit se terminer par une barre oblique. Ceci se résout en la valeur de la propriété **Output Directory** . N’utilisez pas **$(IntDir)** pour définir cette propriété.|
|**$(Platform)**|Nom de la plateforme de projet actuelle, par exemple, « Win32 ».|
|**$(ProjectDir)**|Répertoire du projet (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(ProjectExt)**|L’extension de fichier du projet. Elle inclut le point (« . ») avant l’extension de fichier.|
|**$(ProjectFileName)**|Le nom de fichier du projet (défini comme étant nom de base + extension de fichier).|
|**$(ProjectName)**|Le nom de base du projet.|
|**$(ProjectPath)**|Le nom du chemin absolu du projet (défini comme étant lecteur + chemin + nom de base + extension de fichier).|
|**$(RemoteMachine)**|Définit sur la valeur de la propriété **Remote Machine** sur la page des propriétés du débogage. Pour plus d’informations, consultez [Modification des paramètres du projet pour une configuration Debug C ou C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$(RootNameSpace)**|L’espace de noms, s’il y en a un, contenant l’application.|
|**$(SolutionDir)**|Répertoire de la solution (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ». Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionExt)**|L’extension de fichier de la solution. Elle inclut le point (« . ») avant l’extension de fichier. Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionFileName)**|Le nom de fichier de la solution (défini comme étant nom de base + extension de fichier). Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionName)**|Le nom de base de la solution. Défini uniquement quand une solution est générée dans l’IDE.|
|**$(SolutionPath)**|Le nom du chemin absolu de la solution (défini comme étant lecteur + chemin + nom de base + extension de fichier). Défini uniquement quand une solution est générée dans l’IDE.|
|**$(TargetDir)**|Répertoire du fichier de sortie principal pour la build (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ».|
|**$(TargetExt)**|L’extension de fichier du fichier de sortie principal pour la build. Elle inclut le point (« . ») avant l’extension de fichier.|
|**$(TargetFileName)**|Le nom de fichier du fichier de sortie principal pour la build (défini comme étant nom de base + extension de fichier).|
|**$(TargetName)**|Le nom de base du fichier de sortie principal pour la build.|
|**$(TargetPath)**|Le nom du chemin absolu du fichier de sortie principal pour la build (défini comme étant lecteur + chemin + nom de base + extension de fichier).|
|**$(VCInstallDir)**|Répertoire qui comprend le contenu C++ de votre installation de Visual Studio. Cette propriété contient la version de l’ensemble d’outils Visual C++ ciblé, qui peut être différente de celle du Visual Studio hôte. Par exemple, quand la génération s’effectue avec `$(PlatformToolset) = v140`, **$(VCInstallDir)** contient le chemin d’installation de Visual C++ 2015.|
|**$(VSInstallDir)**|Le répertoire où vous avez installé Visual Studio. Cette propriété contient la version de l’ensemble d’outils Visual Studio ciblé, qui peut être différente de celle du Visual Studio hôte. Par exemple, lors d’une génération avec `$(PlatformToolset) = v110`, **$(VSInstallDir)** contient le chemin de l’installation de Visual Studio 2012.|
|**$(WebDeployPath)**|Le chemin relatif à partir de la racine du déploiement auquel les sorties du projet appartiennent. Retourne la même valeur que <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(WebDeployRoot)**|Chemin absolu de l’emplacement de **\<localhost>**. Par exemple, c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Macros obsolètes

Le système de build pour C++ a considérablement changé entre Visual Studio 2008 et Visual Studio 2010. Plusieurs macros utilisées dans les types de projet antérieurs ont été remplacées par de nouvelles macros. Ces macros ne sont plus utilisées ou ont été remplacées par une ou plusieurs propriétés ou valeurs de [macro de métadonnées d’élément](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_nom_**)**) équivalentes. Les macros marquées comme « migrées » peuvent être mises à jour par l’outil de migration de projet. Si le projet contenant la macro migre depuis Visual Studio 2008 ou une version antérieure vers Visual Studio 2010, Visual Studio convertit la macro en macro actuelle équivalente. Les versions ultérieures de Visual Studio ne peuvent pas convertir des projets Visual Studio 2008 et antérieur en nouveau type de projet. Vous devez convertir ces projets en deux temps ; tout d’abord, convertissez-les en Visual Studio 2010, puis convertissez le résultat en version récente de Visual Studio. Pour plus d’informations, consultez [Vue d’ensemble des problèmes de mise à niveau potentiels](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Description|
|-----------|-----------------|
|**$(InputDir)**|(Migré.) Répertoire du fichier d’entrée (défini au format lecteur + chemin), se termine par une barre oblique inverse « \\ ». Si le projet est l’entrée, cette macro est équivalente à **$(ProjectDir)**.|
|**$(InputExt)**|(Migré.) L’extension de fichier du fichier d’entrée. Elle inclut le point (« . ») avant l’extension de fichier. Si le projet est l’entrée, cette macro est équivalente à **$(ProjectExt)**. Pour les fichiers sources, il s’agit de **%(Extension)**.|
|**$(InputFileName)**|(Migré.) Le nom de fichier du fichier d’entrée (défini comme étant nom de base + extension de fichier). Si le projet est l’entrée, cette macro est équivalente à **$(ProjectFileName)**. Pour les fichiers sources, il s’agit de **%(Identity)**.|
|**$(InputName)**|(Migré.) Nom de base du fichier d’entrée. Si le projet est l’entrée, cette macro est équivalente à **$(ProjectName)**. Pour les fichiers sources, il s’agit de **%(Filename)**.|
|**$(InputPath)**|(Migré.) Le nom du chemin absolu du fichier d’entrée (défini comme étant lecteur + chemin + nom de base + extension de fichier). Si le projet est l’entrée, cette macro est équivalente à **$(ProjectPath)**. Pour les fichiers sources, il s’agit de **%(FullPath)**.|
|**$(ParentName)**|Nom de l’élément contenant cet élément de projet. Il s’agira du nom du dossier parent ou du nom du projet.|
|**$(SafeInputName)**|Le nom du fichier sous forme de nom de classe valide, moins l’extension de fichier. Cette propriété n’a pas d’équivalent exact.|
|**$(SafeParentName)**|Le nom du parent immédiat dans un format de nom valide. Par exemple, une forme est le parent d’un fichier .resx. Cette propriété n’a pas d’équivalent exact.|
|**$(SafeRootNamespace)**|Le nom de l’espace de noms où les Assistants Projet ajouteront le code. Cet espace de noms contiendra seulement des caractères qui sont autorisés dans un identificateur C++ valide. Cette propriété n’a pas d’équivalent exact.|

## <a name="see-also"></a>Voir aussi

- [Projets Visual Studio - C++](../creating-and-managing-visual-cpp-projects.md)
- [Guide du portage et de la mise à niveau de Visual C++](../../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Vue d’ensemble des problèmes de mise à niveau potentiels](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
