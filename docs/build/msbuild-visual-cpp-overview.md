---
title: Vue d’ensemble de MSBuild (Visual C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe3499cdd8f9a9a1cfb91a45e9f039e1b8be2e76
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039087"
---
# <a name="msbuild-visual-c-overview"></a>Vue d'ensemble de MSBuild (Visual C++)  
  
MSBuild est le système pour les projets Visual C++ de génération de la norme. Lorsque vous générez un projet dans l’environnement de développement intégré (IDE) Visual Studio, il utilise l’outil msbuild.exe, un fichier de projet XML et les fichiers de paramètres facultatifs. Bien que vous pouvez utiliser msbuild.exe et un fichier de projet sur la ligne de commande, l’IDE fournit une interface utilisateur afin que vous puissiez plus facilement configurer les paramètres et générez un projet. Cette vue d’ensemble décrit la manière dont Visual C++ utilise le système MSBuild.  
  
## <a name="prerequisites"></a>Prérequis  
  
Lisez les documents suivants à propos de MSBuild.  
  
- [MSBuild](/visualstudio/msbuild/msbuild)  
 Vue d’ensemble des concepts MSBuild.  
  
- [Informations de référence sur MSBuild](/visualstudio/msbuild/msbuild-reference)  
 Informations de référence sur le système MSBuild.  
  
- [Référence du schéma de fichier projet](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 Répertorie les éléments de schémas XML MSBuild, ainsi que leurs attributs et des éléments parents et enfants. Notez en particulier le [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [cible](/visualstudio/msbuild/target-element-msbuild), et [tâche](/visualstudio/msbuild/task-element-msbuild) éléments.  
  
- [Informations de référence sur la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference)  
 Décrit les arguments de ligne de commande et les options que vous pouvez utiliser avec msbuild.exe.  
  
- [Task Reference (Informations de référence sur les tâches MSBuild)](/visualstudio/msbuild/msbuild-task-reference)  
 Décrit les tâches MSBuild. Notez en particulier de ces tâches, qui sont spécifiques à Visual C++ : [BSCMAKE, tâche](/visualstudio/msbuild/bscmake-task), [CL, tâche](/visualstudio/msbuild/cl-task), [CPPClean, tâche](/visualstudio/msbuild/cppclean-task), [LIB (tâche)](/visualstudio/msbuild/lib-task), [Lier tâche](/visualstudio/msbuild/link-task), [MIDL (tâche)](/visualstudio/msbuild/midl-task), [MT, tâche](/visualstudio/msbuild/mt-task), [RC, tâche](/visualstudio/msbuild/rc-task), [setenv, tâche](/visualstudio/msbuild/setenv-task), [ VCMessage, tâche](/visualstudio/msbuild/vcmessage-task), [XDCMake, tâche](/visualstudio/msbuild/xdcmake-task), [tâche XSD](/visualstudio/msbuild/xsd-task).  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild sur la ligne de commande  
  
L’instruction suivante à partir de la [référence de ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) montre que l’outil msbuild.exe prend un implicite ou explicite *project_file* argument (fichier .vcxproj pour les projets Visual C++) et zéro ou plus de la ligne de commande *options* arguments.  
  
> **MSBuild.exe** [ *project_file* ] [ *options* ]  
  
Utilisez le **/target** (ou **/t**) et **cette propriété** (ou **/p**) les options de ligne de commande pour remplacer les propriétés spécifiques et les cibles spécifié dans le fichier projet.  
  
Des fonctions essentielles du fichier projet consiste à spécifier un *cible*, qui est une opération spécifique appliquée à votre projet et les entrées et les sorties qui sont requis pour effectuer cette opération. Un fichier de projet peut spécifier une ou plusieurs cibles, qui peuvent inclure une cible par défaut.  
  
Chaque cible se compose d’une séquence d’un ou plusieurs *tâches*. Chaque tâche est représentée par une classe .NET Framework qui contient une commande exécutable. Par exemple, le [CL, tâche](/visualstudio/msbuild/cl-task) contient le [cl.exe](../build/reference/compiling-a-c-cpp-program.md) commande.  
  
A *paramètre de tâche* est une propriété de la tâche de classe et représente généralement une option de ligne de commande de la commande exécutable. Par exemple, le `FavorSizeOrSpeed` paramètre de la `CL` tâche correspond à la **/Os** et **/Ot** options du compilateur.  
  
Paramètres de tâche supplémentaires prennent en charge l’infrastructure de MSBuild. Par exemple, le `Sources` paramètre de la tâche spécifie un ensemble de tâches qui peuvent être utilisés par d’autres tâches. Pour plus d’informations sur les tâches MSBuild, consultez [référence des tâches](/visualstudio/msbuild/msbuild-task-reference).  
  
La plupart des tâches requièrent des entrées et sorties, telles que les noms de fichiers, chemins d’accès et chaîne, numériques ou booléennes paramètres. Par exemple, une entrée commune est le nom d’un fichier de source .cpp à compiler. Un paramètre d’entrée important est une chaîne qui spécifie la configuration de build et de plateforme, par exemple, « débogage\|Win32 ». Entrées et sorties sont spécifiées par un ou plusieurs XML défini par l’utilisateur `Item` éléments contenus dans un `ItemGroup` élément.  
  
Un fichier projet peut également spécifier défini par l’utilisateur *propriétés* et `ItemDefinitionGroup` *éléments*. Propriétés et éléments forment des paires nom/valeur qui peuvent être utilisés en tant que variables dans la build. Le composant de nom d’une paire définit un *macro*, et le composant de valeur déclare la *valeur macro*. Une macro de propriété est accessible à l’aide de $(*nom*), de notation et d’une macro d’élément est accessible à l’aide de %(*nom*) notation.  
  
Autres éléments XML dans un fichier projet peuvent tester des macros, puis conditionnellement définir la valeur de n’importe quelle macro ou contrôler l’exécution de la build. Noms de macros et les chaînes littérales peuvent être concaténées pour générer des constructions telles que d’un chemin d’accès et nom de fichier. Sur la ligne de commande, le **cette propriété** option définit ou substitue une propriété de projet. Impossible de référencer les éléments sur la ligne de commande.  
  
Le système MSBuild peut exécuter de manière conditionnelle une cible avant ou après une autre cible. En outre, le système peut générer une cible si les fichiers que la cible consomme sont plus récents que les fichiers qu’elle émet.  
  
## <a name="msbuild-in-the-ide"></a>MSBuild dans l’IDE  
  
Lorsque vous définissez des propriétés de projet dans l’IDE et puis enregistrez le projet, Visual C++ écrit les paramètres du projet dans votre fichier projet. Le fichier projet contienne des paramètres qui sont uniques à votre projet, mais il ne contient pas tous les paramètres qui sont requis pour générer votre projet. Le fichier projet contient `Import` les éléments qui incluent un réseau d’autres *fichiers de support.* Les fichiers de support contiennent les propriétés, les cibles et les paramètres qui sont requis pour générer le projet restants.  
  
La plupart des cibles et des propriétés dans les fichiers de prise en charge existent uniquement pour implémenter le système de génération. La section suivante décrit certaines cibles et propriétés utiles que vous pouvez spécifier sur la ligne de commande MSBuild. Pour découvrir les autres cibles et propriétés, explorez les fichiers dans les répertoires de fichiers de prise en charge.  
  
### <a name="support-file-directories"></a>Répertoires de fichiers de prise en charge  
  
Par défaut, les fichiers de prise en charge de Visual C++ principales sont situés dans les répertoires suivants. Les répertoires sous Microsoft Visual Studio sont utilisées par Visual Studio 2017 et versions ultérieures, alors que les répertoires sous MSBuild sont utilisés par Visual Studio 2015 et versions antérieures.  
  
|Répertoire|Description|  
|---------------|-----------------|  
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*version*\ |Contient les fichiers cibles (.targets) et les fichiers de propriétés (.props) qui sont utilisés par les cibles. Par défaut, la macro $ (VCTargetsPath) fait référence à ce répertoire.|  
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ Plateformes\\*plateforme*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\ |Contient les fichiers spécifiques à la plateforme cible et la propriété qui substituent les cibles et les propriétés de son répertoire parent. Ce répertoire contient également une DLL qui définit les tâches qui sont utilisés par les cibles dans ce répertoire.<br /><br /> Le *plateforme* espace réservé représente le ARM, Win32 ou x64 sous-répertoire.|  
|*lecteur*: \Program Files *(x86)* \Microsoft Visual Studio\\*année*\\*édition*\Common7\IDE\VC\VCTargets\ Plateformes\\*plateforme*\PlatformToolsets\\*ensemble d’outils*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*plateforme*\ Ensemble\\*ensemble d’outils*\ <br /><br />*lecteur*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plateforme*\PlatformToolsets\\*ensemble d’outils*\ |Contient les répertoires qui permettent de générer des applications Visual C++ à l’aide de l’élément spécifié de la build *ensemble d’outils*.<br /><br /> Le *année* et *édition* espaces réservés sont utilisés par Visual Studio 2017 et éditions ultérieures. Le *version* espace réservé est V110 pour Visual Studio 2012, V120 pour Visual Studio 2013 ou V140 pour Visual Studio 2015. Le *plateforme* espace réservé représente le ARM, Win32 ou x64 sous-répertoire. Le *ensemble d’outils* espace réservé représente le sous-répertoire ensemble d’outils, par exemple, v140 pour la création d’applications Windows à l’aide de l’ensemble d’outils Visual Studio 2015, v120_xp de génération pour Windows XP à l’aide de l’ensemble d’outils Visual Studio 2013, ou v110_wp80 à générer des applications Windows Phone 8.0 à l’aide de l’ensemble d’outils de Visual Studio 2012.<br /><br />Le chemin d’accès qui contient les répertoires qui permettent la génération de générer des applications Visual C++ 2008 ou de Visual C++ 2010 n’inclut pas le *version*et le *plateforme* espace réservé représente Itanium, Win32 ou x64 sous-répertoire. Le *ensemble d’outils* espace réservé représente le sous-répertoire v90 ou v100 ensemble d’outils.|  
  
### <a name="support-files"></a>Fichiers de prise en charge  
  
Les répertoires de fichiers de prise en charge contiennent des fichiers avec ces extensions :  
  
|Extension|Description|  
|---------------|-----------------|  
|.targets|Contient des `Target` des éléments XML qui spécifient les tâches qui sont exécutées par la cible. Peut également contenir `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`, définies par l’utilisateur `Item` les éléments qui sont utilisés pour assigner des fichiers et des options de ligne de commande pour les paramètres de la tâche.<br /><br /> Pour plus d’informations, consultez [Target, élément (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|  
|.props|Contient `Property Group` définies par l’utilisateur `Property` les éléments XML qui spécifient des fichiers et des paramètres qui sont utilisés pendant une génération.<br /><br /> Peut également contenir `ItemDefinitionGroup` définies par l’utilisateur `Item` les éléments XML qui spécifient les paramètres supplémentaires. Les éléments définis dans un groupe de définitions d’élément sont semblables aux propriétés, mais ne sont pas accessibles à partir de la ligne de commande. Fichiers projet Visual C++ utilisent fréquemment des éléments au lieu des propriétés pour représenter les paramètres.<br /><br /> Pour plus d’informations, consultez [ItemGroup, élément (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup, élément (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), et [élément, élément (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|  
|.Xml|Contient des éléments XML qui déclarent et initialiser les éléments d’interface utilisateur IDE telles que feuilles de propriétés et les pages de propriétés et les contrôles de zone de liste et de la zone de texte.<br /><br /> Les fichiers .xml prennent directement en charge l’IDE mais pas MSBuild. Toutefois, les valeurs des propriétés de l’IDE sont affectées pour générer des propriétés et des éléments.<br /><br /> La plupart des fichiers .xml sont dans un sous-répertoire spécifique aux paramètres régionaux. Par exemple, les fichiers pour la région anglais (États-Unis) sont dans $(VCTargetsPath) \1033\\.|  
  
## <a name="user-targets-and-properties"></a>Propriétés et les cibles de l’utilisateur  
  
Pour utiliser MSBuild plus efficacement sur la ligne de commande, il est utile de connaître les propriétés et cibles sont utiles et pertinentes. La plupart des propriétés et des cibles aident à implémenter le système de génération Visual C++ et par conséquent, ne sont pas pertinentes pour l’utilisateur. Cette section décrit certaines propriétés judicieux d’utilisateur et les cibles.  

### <a name="platformtoolset-property"></a>Propriété PlatformToolset  
  
Le `PlatformToolset` propriété détermine l’ensemble d’outils Visual C++ est utilisé dans la build. Par défaut, l’ensemble d’outils actuel est utilisé. Lorsque cette propriété est définie, la valeur de la propriété est concaténée avec des chaînes littérales pour former le chemin d’accès d’un répertoire qui contient les fichiers cible et de propriété qui sont requises pour générer un projet pour une plateforme particulière. L’ensemble d’outils de plateforme doit être installé pour générer à l’aide de cette version d’ensemble d’outils de plateforme.  
  
Par exemple, définissez la `PlatformToolset` propriété `v140` à utiliser les bibliothèques et les outils de Visual C++ 2015 pour générer votre application :  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>Propriété de PreferredToolArchitecture  
  
Le `PreferredToolArchitecture` propriété détermine si le compilateur 32 bits ou 64 bits et les outils sont utilisés dans la build. Cette propriété n’affecte pas l’architecture de plateforme de sortie ou de configuration. Par défaut, MSBuild utilise le x86 version du compilateur et des outils si cette propriété n’est pas définie.  
  
Par exemple, définissez la `PreferredToolArchitecture` propriété `x64` à utiliser le compilateur 64 bits et les outils pour générer votre application :  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>Propriété UseEnv  
  
Par défaut, les paramètres spécifiques à la plateforme pour le projet actuel substituent les variables d’environnement PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION et de plateforme. Définir le `UseEnv` propriété `true` afin de garantir que les variables d’environnement ne sont pas substitués.  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>Cibles  
  
Il existe des centaines de cibles dans les fichiers de prise en charge de Visual C++. Toutefois, la plupart sont des cibles orientées système que l’utilisateur peut ignorer. La plupart des cibles système sont préfixées par un trait de soulignement (_), ou avoir un nom commençant par « PrepareFor », « Calcul », « Avant », « After », « Pre » ou « Post ».  
  
Le tableau suivant répertorie plusieurs cibles orientées utilisateur utiles.  
  
|une cible|Description|  
|------------|-----------------|  
|BscMake|Exécute l’outil Microsoft Browse Information Maintenance Utility, bscmake.exe.|  
|Générer|Génère le projet.<br /><br /> Il s’agit de la cible par défaut pour un projet.|  
|ClCompile|Exécute l’outil du compilateur Visual C++, cl.exe.|  
|Nettoyer|Fichiers de génération supprime temporaires et intermédiaires.|  
|Lib|Exécute l’outil Gestionnaire de bibliothèque Microsoft 32 bits, lib.exe.|  
|Lien|Exécute l’outil de l’éditeur de liens Visual C++, link.exe.|  
|ManifestResourceCompile|Extrait une liste de ressources à partir d’un manifeste, puis exécute l’outil compilateur de ressources Microsoft Windows, rc.exe.|  
|MIDL|Exécute l’outil compilateur MIDL Microsoft Interface Definition Language (), midl.exe.|  
|Rebuild|Nettoie puis génère votre projet|  
|ResourceCompile|Exécute l’outil compilateur de ressources Microsoft Windows, rc.exe.|  
|XdcMake|Exécute l’outil de Documentation XML, xdcmake.exe.|  
|XSD|Exécute l’outil XML Schema Definition, xsd.exe. *Voir la Remarque ci-dessous.*|  

> [!NOTE] 
> Dans Visual Studio 2017, prise en charge de projet C++ **xsd** fichiers est déconseillée. Vous pouvez toujours utiliser **Microsoft.VisualC.CppCodeProvider** en ajoutant **CppCodeProvider.dll** manuellement dans le GAC.
  
## <a name="see-also"></a>Voir aussi  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
