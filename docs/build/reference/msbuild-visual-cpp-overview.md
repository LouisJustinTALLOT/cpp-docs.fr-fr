---
title: Les projets internes de MSBuild pour C++ dans Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 6c8e891f6bf6ed6b3bb3d1c84dbc13b64ab7b868
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021902"
---
# <a name="msbuild-internals-for-c-projects"></a>Éléments internes de MSBuild pour les projets C++

Lorsque vous définissez les propriétés du projet dans l’IDE et puis enregistrez le projet, Visual Studio écrit les paramètres du projet dans votre fichier projet. Le fichier projet contient des paramètres qui sont uniques à votre projet, mais il ne contient pas tous les paramètres qui sont requis pour générer votre projet. Le fichier projet contient `Import` éléments qui incluent un réseau d’autres *prennent en charge des fichiers.* Les fichiers de support contiennent les propriétés, les cibles et les paramètres qui sont obligatoires pour générer le projet restants.

La plupart des cibles et propriétés dans les fichiers de support ont pour seul but d’implémenter le système de génération. La section suivante décrit certaines cibles et propriétés utiles que vous pouvez spécifier sur la ligne de commande MSBuild. Pour découvrir les autres cibles et propriétés, explorez les fichiers dans les répertoires de fichiers de prise en charge.

## <a name="support-file-directories"></a>Répertoires de fichiers de prise en charge

Par défaut, les fichiers de prise en charge de Visual Studio principales sont situés dans les répertoires suivants. Les répertoires sous Microsoft Visual Studio sont utilisées par Visual Studio 2017 et versions ultérieures, tandis que les répertoires sous MSBuild sont utilisés par Visual Studio 2015 et versions antérieures.

|Répertoire|Description|
|---------------|-----------------|
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*version*\ |Contient les fichiers cibles (.targets) et les fichiers de propriétés (.props) qui sont utilisés par les cibles. Par défaut, la macro $ (VCTargetsPath) référence ce répertoire.|
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ Plateformes\\*plateforme*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\ |Contient les fichiers spécifiques à la plateforme cible et la propriété qui substituent les cibles et propriétés dans son répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisés par les cibles dans ce répertoire.<br /><br /> Le *plateforme* espace réservé représente le ARM, Win32 ou x64 sous-répertoire.|
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ Plateformes\\*plateforme*\PlatformToolsets\\*ensemble d’outils*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\ Ensemble\\*ensemble d’outils*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plateforme*\PlatformToolsets\\*ensemble d’outils*\ |Contient les répertoires qui permettent la génération générer des applications C++ en utilisant le *ensemble d’outils*.<br /><br /> Le *année* et *édition* des espaces réservés sont utilisés par Visual Studio 2017 et versions ultérieures. Le *version* espace réservé est V110 pour Visual Studio 2012, V120 pour Visual Studio 2013 ou V140 pour Visual Studio 2015. Le *plateforme* espace réservé représente le ARM, Win32 ou x64 sous-répertoire. Le *ensemble d’outils* espace réservé représente le sous-répertoire d’ensemble d’outils, par exemple, v140 pour la création d’applications de Windows à l’aide de l’ensemble d’outils Visual Studio 2015, v120_xp pour générer pour XP de Windows à l’aide de l’ensemble d’outils Visual Studio 2013, ou v110_wp80 à créer des applications Windows Phone 8.0 à l’aide de l’ensemble d’outils de Visual Studio 2012.<br /><br />Le chemin d’accès qui contient les répertoires qui permettent la génération générer des applications Visual Studio 2008 ou Visual Studio 2010 n’inclut pas le *version*et le *plateforme* espace réservé représente l’Itanium, Win32 ou x64 sous-répertoire. Le *ensemble d’outils* espace réservé représente le sous-répertoire d’ensemble d’outils v90 ou v100.|

## <a name="support-files"></a>Fichiers de prise en charge

Les répertoires de fichiers de support contiennent des fichiers avec ces extensions :

|Extension|Description|
|---------------|-----------------|
|.targets|Contient `Target` les éléments XML qui spécifient les tâches qui sont exécutées par la cible. Peut également contenir `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`, définis par l’utilisateur `Item` éléments qui sont utilisés pour assigner des fichiers et des options de ligne de commande aux paramètres de tâche.<br /><br /> Pour plus d’informations, consultez [Target, élément (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Contient `Property Group` définis par l’utilisateur `Property` les éléments XML qui spécifient des fichiers et des paramètres qui sont utilisés pendant une génération.<br /><br /> Peut également contenir `ItemDefinitionGroup` définis par l’utilisateur `Item` les éléments XML qui spécifient des paramètres supplémentaires. Les éléments définis dans un groupe de définitions d’élément sont similaires aux propriétés, mais ne sont pas accessibles à partir de la ligne de commande. Les fichiers de projet Visual Studio utilisent fréquemment des éléments au lieu de propriétés pour représentent les paramètres.<br /><br /> Pour plus d’informations, consultez [ItemGroup, élément (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[ItemDefinitionGroup, élément (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), et [Item, élément (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Contient des éléments XML qui déclarent et initialisent des éléments d’interface utilisateur IDE tels que des feuilles de propriétés et les pages de propriétés et les contrôles de zone de liste et de la zone de texte.<br /><br /> Les fichiers .xml prennent directement en charge l’IDE mais pas MSBuild. Toutefois, les valeurs des propriétés IDE sont assignées pour générer des propriétés et des éléments.<br /><br /> La plupart des fichiers .xml se trouvent dans un sous-répertoire spécifique aux paramètres régionaux. Par exemple, les fichiers pour la région États-Unis de l’anglais sont dans $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Cibles et propriétés utilisateur

Pour utiliser MSBuild plus efficacement sur la ligne de commande, il est utile de connaître les propriétés et cibles sont utiles et pertinentes. La plupart des propriétés et cibles aident à implémenter le système de génération Visual Studio et par conséquent, ne sont pas pertinentes pour l’utilisateur. Cette section décrit certaines des propriétés orientées utilisateur utiles et des cibles.

### <a name="platformtoolset-property"></a>Propriété PlatformToolset

Le `PlatformToolset` propriété détermine quel ensemble d’outils MSVC est utilisée dans la build. Par défaut, l’ensemble d’outils actuel est utilisé. Lorsque cette propriété est définie, la valeur de la propriété est concaténée avec des chaînes littérales pour former le chemin d’accès d’un répertoire qui contient les fichiers de propriété et la cible sont requis pour générer un projet à une plateforme spécifique. L’ensemble d’outils de plateforme doit être installé pour générer à l’aide de cette version d’ensemble d’outils de plateforme.

Par exemple, définissez la `PlatformToolset` propriété `v140` à utiliser les bibliothèques et les outils de Visual Studio 2015 pour générer votre application :

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Propriété PreferredToolArchitecture

Le `PreferredToolArchitecture` propriété détermine si le compilateur 32 bits ou 64 bits et les outils sont utilisés dans la build. Cette propriété n’affecte pas l’architecture de plateforme de sortie ou la configuration. Par défaut, MSBuild utilise le x86 version du compilateur et des outils si cette propriété n’est pas définie.

Par exemple, définissez la `PreferredToolArchitecture` propriété `x64` à utiliser le compilateur 64 bits et outils pour générer votre application :

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Propriété UseEnv

Par défaut, les paramètres spécifiques à la plateforme pour le projet actuel substituent les variables d’environnement PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION et plateforme. Définir le `UseEnv` propriété **true** afin de garantir que les variables d’environnement ne sont pas remplacées.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cibles

Il existe des centaines de cibles dans les fichiers de prise en charge de Visual Studio. Toutefois, la plupart sont des cibles orientées système que l’utilisateur peut ignorer. La plupart des cibles système sont préfixées par un trait de soulignement (_), ou avoir un nom qui commence par « PrepareFor », « Compute », « Before », « After », « Pre » ou « Post ».

Le tableau suivant répertorie plusieurs cibles orientées utilisateur utiles.

|une cible|Description|
|------------|-----------------|
|BscMake|Exécute l’outil Microsoft Browse Information Maintenance Utility, bscmake.exe.|
|Build|Génère le projet.<br /><br /> Il s’agit de la cible par défaut pour un projet.|
|ClCompile|Exécute le compilateur MSVC, cl.exe.|
|Nettoyer|Fichiers de génération de suppressions temporaires et intermédiaires.|
|Lib|Exécute l’outil Gestionnaire de bibliothèque Microsoft 32 bits, lib.exe.|
|Lien|Exécute l’outil de l’éditeur de liens MSVC, link.exe.|
|ManifestResourceCompile|Extrait une liste de ressources à partir d’un manifeste, puis exécute l’outil compilateur de ressources Microsoft Windows, rc.exe.|
|Midl|Exécute le compilateur Microsoft Interface Definition Language (MIDL), midl.exe.|
|Rebuild|Nettoie, puis génère votre projet.|
|ResourceCompile|Exécute l’outil compilateur de ressources Microsoft Windows, rc.exe.|
|XdcMake|Exécute l’outil XML Documentation, xdcmake.exe.|
|Xsd|Exécute l’outil XML Schema Definition, xsd.exe. *Voir la remarque ci-dessous.*|

> [!NOTE]
> Dans Visual Studio 2017, C++ projet prise en charge de **xsd** fichiers est déconseillée. Vous pouvez toujours utiliser **Microsoft.VisualC.CppCodeProvider** en ajoutant **CppCodeProvider.dll** manuellement dans le GAC.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches MSBuild](/visualstudio/msbuild/msbuild-task-reference)<br/>
[BscMake, tâche](/visualstudio/msbuild/bscmake-task)<br/>
[CL, tâche](/visualstudio/msbuild/cl-task)<br/>
[CPPClean, tâche](/visualstudio/msbuild/cppclean-task)<br/>
[LIB, tâche](/visualstudio/msbuild/lib-task)<br/>
[Lier, tâche](/visualstudio/msbuild/link-task)<br/>
[MIDL, tâche](/visualstudio/msbuild/midl-task)<br/>
[MT, tâche](/visualstudio/msbuild/mt-task)<br/>
[RC, tâche](/visualstudio/msbuild/rc-task)<br/>
[SetEnv Task](/visualstudio/msbuild/setenv-task)<br/>
[VCMessage, tâche](/visualstudio/msbuild/vcmessage-task)<br/>
[XDCMake, tâche](/visualstudio/msbuild/xdcmake-task)<br/>
