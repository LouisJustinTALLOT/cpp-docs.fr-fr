---
title: Composants internes MSBuild pour les projets C++ dans Visual Studio
ms.date: 05/16/2019
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: b3348320a1468fea03f39e43cc847f1085f3d319
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837232"
---
# <a name="msbuild-internals-for-c-projects"></a>Composants internes MSBuild pour les projets C++

Quand vous définissez des propriétés de projet dans l’IDE et enregistrez le projet, Visual Studio écrit les paramètres du projet dans votre fichier projet. Le fichier projet contient des paramètres qui sont propres à votre projet, mais il ne contient pas tous les paramètres qui sont nécessaires pour générer votre projet. Le fichier projet contient des éléments `Import` qui incluent un réseau d’autres *fichiers de support*. Les fichiers de support contiennent les propriétés, cibles et paramètres restants qui sont obligatoires pour générer le projet.

La plupart des cibles et propriétés dans les fichiers de support ont pour seul but d’implémenter le système de build. La section suivante décrit certaines cibles et propriétés utiles que vous pouvez spécifier sur la ligne de commande MSBuild. Pour découvrir d’autres cibles et propriétés, explorez les fichiers dans les répertoires des fichiers de support.

## <a name="support-file-directories"></a>Répertoires des fichiers de support

Par défaut, les principaux fichiers de support Visual Studio sont situés dans les répertoires suivants. Les répertoires sous Microsoft Visual Studio sont utilisés par Visual Studio 2017 et ultérieur, tandis que les répertoires sous MSBuild sont utilisés par Visual Studio 2015 et antérieur.

|Répertoire|Description|
|---------------|-----------------|
|*lecteur*:\Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ <br /><br />*lecteur*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*version*\ |Contient les principaux fichiers cibles (.targets) et fichiers de propriétés (.props) qui sont utilisés par les cibles. Par défaut, la macro $(VCTargetsPath) référence ce répertoire.|
|*lecteur*:\Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\Platforms\\*plateforme*\ <br /><br />*lecteur*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\ |Contient les fichiers cibles et de propriétés spécifiques à la plateforme qui remplacent les cibles et propriétés dans le répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisées par les cibles dans ce répertoire.<br /><br /> L’espace réservé *plateforme* représente le sous-répertoire ARM, Win32 ou x64.|
|*lecteur*:\Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\Platforms\\*plateforme*\PlatformToolsets\\*ensemble_outils*\ <br /><br />*lecteur*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\PlatformToolsets\\*ensemble_outils*\ <br /><br />*lecteur*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plateforme*\PlatformToolsets\\*ensemble_outils*\ |Contient les répertoires qui permettent de générer des applications C++ en utilisant l’*ensemble d’outils* spécifié.<br /><br /> Les espaces réservés *année* et *édition* sont utilisés par Visual Studio 2017 et ultérieur. L’espace réservé *version* correspond à V110 pour Visual Studio 2012, V120 pour Visual Studio 2013, V140 pour Visual Studio 2015, v141 pour Visual Studio 2017 et v142 pour Visual Studio 2019. L’espace réservé *plateforme* représente le sous-répertoire ARM, Win32 ou x64. L’espace réservé *ensemble_outils* représente le sous-répertoire de l’ensemble d’outils, par exemple v140 pour la génération d’applications Windows à l’aide de l’ensemble d’outils Visual Studio 2015, v120_xp afin de générer pour Windows XP à l’aide de l’ensemble d’outils Visual Studio 2013.<br /><br />Le chemin qui contient les répertoires qui permettent de générer des applications Visual Studio 2008 ou Visual Studio 2010 n’inclut pas l’espace réservé *version*et l’espace réservé *plateforme* représente le sous-répertoire Itanium, Win32 ou x64. L’espace réservé *ensemble_outils* représente le sous-répertoire de l’ensemble d’outils v90 ou v100.|

## <a name="support-files"></a>Fichiers de support

Les répertoires des fichiers de support contiennent des fichiers avec les extensions suivantes :

|Extension|Description|
|---------------|-----------------|
|.targets|Contient des éléments XML `Target` qui spécifient les tâches qui sont exécutées par la cible. Peut également contenir des éléments `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup` et `Item` définis par l’utilisateur qui sont utilisés pour assigner des fichiers et des options de ligne de commande aux paramètres de tâche.<br /><br /> Pour plus d’informations, consultez [Target, élément (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Contient des éléments XML `Property` définis par l’utilisateur et `Property Group` qui spécifient des paramètres de fichier et des paramètres qui sont utilisés pendant une génération.<br /><br /> Peut également contenir des éléments XML `Item` définis par l’utilisateur et `ItemDefinitionGroup` qui spécifient des paramètres supplémentaires. Les éléments définis dans un groupe de définitions d’éléments sont similaires aux propriétés, mais ne sont pas accessibles à partir de la ligne de commande. Les fichiers projet Visual Studio utilisent fréquemment des éléments au lieu de propriétés pour représenter les paramètres.<br /><br /> Pour plus d’informations, consultez [ItemGroup, élément (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[ItemDefinitionGroup, élément (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild) et [Item, élément (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Contient des éléments XML qui déclarent et initialisent des éléments d’interface utilisateur IDE tels que des feuilles de propriétés et des pages de propriétés ainsi que des contrôles de zone de liste et de zone de texte.<br /><br /> Les fichiers .xml prennent directement en charge l’IDE, mais pas MSBuild. Toutefois, les valeurs des propriétés IDE sont assignées pour générer des propriétés et des éléments.<br /><br /> La plupart des fichiers .xml se trouvent dans un sous-répertoire spécifique aux paramètres régionaux. Par exemple, les fichiers pour la région English-US figurent dans $(VCTargetsPath)\1033\\.|

## <a name="user-targets-and-properties"></a>Cibles et propriétés utilisateur

Pour utiliser MSBuild plus efficacement sur la ligne de commande, il est judicieux de connaître les propriétés et cibles qui sont utiles et pertinentes. La plupart des propriétés et cibles aident à implémenter le système de build Visual Studio et, par conséquent, ne sont pas pertinentes pour l’utilisateur. Cette section décrit certaines propriétés et cibles utiles orientées utilisateur.

### <a name="platformtoolset-property"></a>Propriété PlatformToolset

La propriété `PlatformToolset` identifie l’ensemble d’outils MSVC utilisé dans la génération. Par défaut, l’ensemble d’outils actuel est utilisé. Lorsque cette propriété est définie, la valeur de la propriété est concaténée avec des chaînes littérales pour former le chemin d’un répertoire qui contient les fichiers de propriété et cibles requis afin de générer un projet pour une plateforme spécifique. L’ensemble d’outils de plateforme doit être installé pour générer à l’aide de cette version d’ensemble d’outils de plateforme.

Par exemple, affectez à la propriété `PlatformToolset` la valeur `v140` afin d’utiliser les bibliothèques et les outils Visual Studio 2015 pour générer votre application :

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Propriété PreferredToolArchitecture

La propriété `PreferredToolArchitecture` détermine si les outils et le compilateur 32 bits ou 64 bits sont utilisés dans la génération. Cette propriété n’affecte pas l’architecture ni la configuration de la plateforme de sortie. Par défaut, MSBuild utilise la version x86 du compilateur et des outils si cette propriété n’est pas définie.

Par exemple, affectez à la propriété `PreferredToolArchitecture` la valeur `x64` afin d’utiliser les outils et le compilateur 64 bits pour générer votre application :

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Propriété UseEnv

Par défaut, les paramètres spécifiques à la plateforme pour le projet actuel substituent les variables d’environnement PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION et PLATFORM. Affectez à la propriété `UseEnv` la valeur **true** afin de garantir que les variables d’environnement ne sont pas remplacées.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cibles

Il existe des centaines de cibles dans les fichiers de support Visual Studio. Toutefois, la plupart sont des cibles orientées système que l’utilisateur peut ignorer. La plupart des cibles système sont préfixées par un trait de soulignement (_), ou ont un nom qui commence par « PrepareFor », « Compute », « Before », « After », « Pre » ou « Post ».

Le tableau suivant liste plusieurs cibles orientées utilisateur utiles.

|une cible|Description|
|------------|-----------------|
|BscMake|Exécute l’outil Microsoft Browse Information Maintenance Utility, bscmake.exe.|
|Générer|Génère le projet.<br /><br /> Il s’agit de la cible par défaut pour un projet.|
|ClCompile|Exécute l’outil Compilateur MSVC, cl.exe.|
|Nettoyer|Supprime les fichiers de génération temporaires et intermédiaires.|
|Lib|Exécute l’outil Gestionnaire de bibliothèques 32 bits de Microsoft, lib.exe.|
|Lien|Exécute l’outil Éditeur de liens MSVC, link.exe.|
|ManifestResourceCompile|Extrait une liste de ressources à partir d’un manifeste, puis exécute l’outil Compilateur de ressources Microsoft Windows, rc.exe.|
|Midl|Exécute l’outil Compilateur MIDL (Microsoft Interface Definition Language), midl.exe.|
|Rebuild|Nettoie, puis génère votre projet.|
|ResourceCompile|Exécute l’outil Compilateur de ressources Microsoft Windows, rc.exe.|
|XdcMake|Exécute l’outil Documentation XML, xdcmake.exe.|
|Xsd|Exécute l’outil XML Schema Definition, xsd.exe. *Voir la remarque ci-dessous.*|

> [!NOTE]
> Dans Visual Studio 2017 et ultérieur, les fichiers **xsd** ne sont plus pris en charge par les projets C++. Vous pouvez toujours utiliser **Microsoft.VisualC.CppCodeProvider** en ajoutant **CppCodeProvider.dll** manuellement au GAC.

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
