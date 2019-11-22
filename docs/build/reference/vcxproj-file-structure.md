---
title: Structure des fichiers .vcxproj et .props
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: a24349980e9395257f20fcfcc0987883060a7c1d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303133"
---
# <a name="vcxproj-and-props-file-structure"></a>Structure des fichiers .vcxproj et .props

[MSBuild](../msbuild-visual-cpp.md) est le système de projet par défaut dans Visual Studio. Quand vous choisissez **Fichier** > **Nouveau projet** dans Visual C++, vous créez un projet MSBuild dont les paramètres sont stockés dans un fichier projet XML portant l’extension `.vcxproj`. Le fichier projet peut également importer des fichiers .props et .targets dans lesquels des paramètres peuvent être stockés. Dans la plupart des cas, il est inutile de modifier manuellement le fichier projet. Toute modification manuelle est même déconseillée, sauf si connaissez bien MSBuild. Utilisez dans la mesure du possible les pages de propriétés de Visual Studio pour modifier les paramètres d’un projet (consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)). Toutefois, dans certains cas, vous pouvez être amené à modifier manuellement un fichier projet ou une feuille de propriétés. Si cela vous concerne, cet article contient des informations de base sur la structure du fichier.

**Important :**

Si vous choisissez de modifier manuellement un fichier .vcxproj, tenez compte des points suivants :

1. La structure du fichier doit suivre un formulaire prescrit qui est décrit dans cet article.

1. Le système de projet Visual Studio C++ ne prend pas actuellement en charge les caractères génériques dans les éléments de projet. L’exemple suivant n’est pas pris en charge :

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Le système de projet Visual Studio C++ ne prend pas actuellement en charge les macros dans les chemins d’éléments de projet. L’exemple suivant n’est pas pris en charge :

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   « pas pris en charge » signifie qu’il n’est pas garanti que les macros fonctionnent pour toutes les opérations dans l’IDE. Les macros qui ne changent pas leur valeur dans des configurations différentes doivent fonctionner, mais elles peuvent ne pas être conservées si un élément est déplacé vers un autre filtre ou projet. Les macros dont la valeur change pour différentes configurations provoquent des problèmes, car l’IDE ne s’attend pas à ce que les chemins d’élément de projet soient différents pour différentes configurations de projet.

1. Pour ajouter, supprimer ou modifier correctement les propriétés du projet quand vous les modifiez dans la boîte de dialogue **Propriétés du projet**, le fichier doit contenir des groupes distincts pour chaque configuration de projet, et les conditions doivent se présenter sous la forme suivante :

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Chaque propriété doit être spécifiée dans le groupe avec l’étiquette appropriée, comme indiqué dans le fichier de règles de propriété. Pour plus d’informations, consultez [Fichiers de règles XML des pages de propriétés](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>Éléments du fichier .vcxproj

Vous pouvez inspecter le contenu d’un fichier .vcxproj à l’aide d’un éditeur de texte ou XML. Pour l’afficher dans Visual Studio, cliquez avec le bouton sur le projet dans l’Explorateur de solutions, choisissez **Décharger le projet**, puis **Modifier Foo.vcxproj**.

Vous pouvez tout de suite remarquer que les éléments de niveau supérieur s’affichent dans un ordre particulier. Par exemple :

- La plupart des groupes de propriétés et des groupes de définitions d’éléments se trouvent après l’importation de Microsoft.Cpp.Default.props.

- Toutes les cibles sont importées à la fin du fichier.

- Plusieurs groupes de propriétés, chacun d’eux ayant une étiquette unique, suivent un ordre particulier.

L’ordre des éléments dans le fichier projet est très important, car MSBuild est basé sur un modèle d’évaluation séquentiel.  Si votre fichier projet, contenant tous les fichiers .props et .targets importés, comprend plusieurs définitions d’une propriété, la dernière définition remplace les précédentes. Dans l’exemple suivant, la valeur « XYZ » est définie lors de la compilation, car le moteur MSBUild le rencontre en dernier lors de son évaluation.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

L’extrait suivant montre un fichier .vcxproj minimal. Tout fichier .vcxproj généré par Visual Studio contient ces éléments MSBuild de niveau supérieur dans cet ordre (bien qu’il puisse contenir plusieurs copies de chaque élément de niveau supérieur). Notez que les attributs `Label` sont des étiquettes arbitraires qui sont uniquement utilisées par Visual Studio en guise de charpentes à des fins de modification (ces attributs n’ont aucune autre fonction).

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

Les sections suivantes décrivent à quoi servent ces éléments et pourquoi ils sont ordonnés de la sorte :

### <a name="project-element"></a>Élément Project

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` est le nœud racine. Il spécifie la version de MSBuild à utiliser, ainsi que la cible par défaut à exécuter quand ce fichier est passé à MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>Élément ItemGroup ProjectConfigurations

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` contient la description de la configuration du projet. Voici quelques exemples : Debug|Win32, Release|Win32, Debug|ARM, etc. De nombreux paramètres de projet sont spécifiques à une configuration donnée. Par exemple, s’il est souhaitable de définir les propriétés d’optimisation d’une version Release, il n’est pas nécessaire de le faire pour une version Debug.

Le groupe d’éléments `ProjectConfigurations` n’est pas utilisé au moment de la génération. L’IDE Visual Studio en a besoin pour charger le projet. Vous pouvez déplacer ce groupe d’éléments dans un fichier .props et l’importer dans le fichier .vcxproj. Toutefois, dans ce cas, si vous devez ajouter ou supprimer des configurations, vous devez modifier manuellement le fichier .props. Vous ne pouvez pas utiliser l’IDE.

### <a name="projectconfiguration-elements"></a>Éléments ProjectConfiguration

L’extrait suivant montre une configuration de projet. Dans cet exemple, "Debug|x64" est le nom de la configuration. Le nom de la configuration du projet doit être au format $(Configuration)|$(Platform). Un nœud ProjectConfiguration peut avoir deux propriétés : Configuration et Platform. Ces propriétés sont automatiquement définies avec les valeurs spécifiées ici quand la configuration est active.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

L’IDE s’attend à trouver une configuration de projet pour toute combinaison de valeurs Configuration et Platform dans l’ensemble des éléments ProjectConfiguration. Cela signifie qu’un projet a souvent des configurations de projet dénuées de sens pour répondre à cette exigence. Par exemple, si un projet a les configurations suivantes :

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

Il doit également avoir ces configurations, bien que « Special 32-bit Optimization » n’ait aucune signification pour x64 :

- Debug|x64

- Retail|x64

- Special 32-bit Optimization|x64

Vous pouvez désactiver les commandes de génération et de déploiement pour n’importe quelle configuration dans le **gestionnaire de configuration de solutions**.

### <a name="globals-propertygroup-element"></a>Élément PropertyGroup Globals

```xml
<PropertyGroup Label="Globals" />
```

`Globals` contient des paramètres au niveau du projet comme ProjectGuid, RootNamespace et ApplicationType/ApplicationTypeRevision. Les deux derniers définissent souvent le système d’exploitation cible. Un projet peut uniquement cibler un système d’exploitation unique dans la mesure où les références et les éléments du projet ne peuvent pas pour l’instant avoir de conditions. Ces propriétés ne sont généralement pas remplacées autre part dans le fichier projet. Ce groupe n’étant pas dépendant de la configuration, il n’y a généralement qu’un seul groupe Globals dans le fichier projet.

### <a name="microsoftcppdefaultprops-import-element"></a>Élément Import Microsoft.Cpp.default.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

La feuille de propriétés **Microsoft.Cpp.default.props** est fournie avec Visual Studio et ne peut pas être modifiée. Elle contient les paramètres par défaut du projet. Les valeurs par défaut peuvent varier en fonction du type d’application.

### <a name="configuration-propertygroup-elements"></a>Éléments PropertyGroup Configuration

```xml
<PropertyGroup Label="Configuration" />
```

Un groupe de propriétés `Configuration` est attaché à une condition de configuration (comme `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`). Plusieurs copies sont disponibles, une par configuration. Ce groupe de propriétés héberge les propriétés définies pour une configuration spécifique. Les propriétés de configuration, dont PlatformToolset, contrôlent également l’inclusion de feuilles de propriétés système dans **Microsoft.Cpp.props**. Par exemple, si vous définissez la propriété `<CharacterSet>Unicode</CharacterSet>`, la feuille de propriétés système **microsoft.Cpp.unicodesupport.props** est incluse. Si vous inspectez **Microsoft.Cpp.props**, vous pouvez voir la ligne suivante : `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />`.

### <a name="microsoftcppprops-import-element"></a>Élément Import Microsoft.Cpp.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

La feuille de propriétés **Microsoft.Cpp.props** définit (directement ou par le biais d’importations) les valeurs par défaut de nombreuses propriétés spécifiques aux outils, comme les propriétés liées à l’optimisation et au niveau d’avertissement du compilateur, la propriété TypeLibraryName de l’outil MIDL, etc. Elle importe également différentes feuilles de propriétés système basées sur les propriétés de configuration définies dans le groupe de propriétés figurant juste au-dessus.

### <a name="extensionsettings-importgroup-element"></a>Élément ImportGroup ExtensionSettings

```xml
<ImportGroup Label="ExtensionSettings" />
```

Le groupe `ExtensionSettings` contient les importations des feuilles de propriétés qui font partie des personnalisations de build. Une personnalisation de build est définie par trois fichiers : un fichier .targets, un fichier .props et un fichier .xml. Ce groupe d’importations contient les importations du fichier .props.

### <a name="propertysheets-importgroup-elements"></a>Éléments ImportGroup PropertySheets

```xml
<ImportGroup Label="PropertySheets" />
```

Le groupe `PropertySheets` contient les importations des feuilles de propriétés d’utilisateur. Il s’agit des feuilles de propriétés que vous ajoutez au moyen de la vue Gestionnaire de propriétés dans Visual Studio. L’ordre dans lequel ces importations sont répertoriées est important et est reflété dans le Gestionnaire de propriétés. Le fichier projet contient normalement plusieurs instances de ce genre de groupe d’importations, une pour chaque configuration de projet.

### <a name="usermacros-propertygroup-element"></a>Élément PropertyGroup UserMacros

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` contient des propriétés que vous créez comme variables pour personnaliser votre processus de génération. Vous pouvez par exemple définir une macro utilisateur pour définir votre chemin de sortie personnalisé, $(CustomOutputPath), et l’utiliser pour définir d’autres variables. Ce groupe de propriétés héberge de telles propriétés. Dans Visual Studio, notez que ce groupe n’est pas rempli dans le fichier projet, car Visual C++ ne prend pas en charge les macros utilisateur pour les configurations. Les macros utilisateur sont prises en charge dans les feuilles de propriétés.

### <a name="per-configuration-propertygroup-elements"></a>Éléments PropertyGroup par configuration

```xml
<PropertyGroup />
```

Il existe plusieurs instances de ce groupe de propriétés, une par configuration de projet. Chaque groupe de propriétés doit être attaché à une condition de configuration. Si une configuration est manquante, la boîte de dialogue **Propriétés du projet** ne fonctionne pas correctement. Contrairement aux groupes de propriétés ci-dessus, celui-ci n’a pas d’étiquette. Ce groupe contient des paramètres au niveau de la configuration du projet. Ces paramètres s’appliquent à tous les fichiers qui font partie du groupe d’éléments spécifié. Les métadonnées de définition des éléments de personnalisation de la build sont initialisées ici.

Ce PropertyGroup doit venir après `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` et il ne doit pas y avoir d’autre PropertyGroup sans étiquette avant (sinon, la modification des propriétés du projet ne fonctionnera pas correctement).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Éléments ItemDefinitionGroup par configuration

```xml
<ItemDefinitionGroup />
```

Contient les définitions d’éléments. Celles-ci doivent suivre les mêmes règles de conditions que les éléments PropertyGroup par configuration sans étiquette.

### <a name="itemgroup-elements"></a>Éléments ItemGroup

```xml
<ItemGroup />
```

Contient les éléments (fichiers sources, etc.) dans le projet. Les conditions ne sont pas prises en charge pour les éléments de projet (à savoir les types d’éléments qui sont considérés comme des éléments de projet par les définitions de règles).

Les métadonnées doivent avoir des conditions de configuration pour chaque configuration, même si elles sont identiques. Par exemple :

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Le système de projet Visual Studio C++ ne prend pas actuellement en charge les caractères génériques dans les éléments de projet.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Le système de projet Visual Studio C++ ne prend pas actuellement en charge les macros dans les éléments de projet.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Les références, spécifiées dans un ItemGroup, présentent ces limitations :

- Les références ne prennent pas en charge les conditions.

- Les métadonnées des références ne prennent pas en charge les conditions.

### <a name="microsoftcpptargets-import-element"></a>Élément Import Microsoft.Cpp.targets

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Définit (directement ou par le biais d’importations) des cibles Visual C++ comme build, clean, etc.

### <a name="extensiontargets-importgroup-element"></a>Élément ImportGroup ExtensionTargets

```xml
<ImportGroup Label="ExtensionTargets" />
```

Ce groupe contient des importations pour les fichiers cibles de personnalisation de la build.

## <a name="impact-of-incorrect-ordering"></a>Impact d’un ordre incorrect

L’IDE Visual Studio dépend de l’ordre des éléments du fichier projet décrit ci-dessus. Par exemple, quand vous définissez une valeur de propriété dans les pages de propriétés, l’IDE place généralement la définition de la propriété dans le groupe de propriétés avec l’étiquette vide. Les valeurs par défaut introduites dans les feuilles de propriétés système sont ainsi remplacées par les valeurs définies par l’utilisateur. De façon similaire, les fichiers cibles sont importés à la fin parce qu’ils utilisent les propriétés définies ci-dessus et qu’ils ne définissent généralement pas de propriétés eux-mêmes. De même, les feuilles de propriétés d’utilisateur sont importées après les feuilles de propriétés système (incluses par le biais de **Microsoft.Cpp.props**). L’utilisateur peut ainsi remplacer les valeurs par défaut introduites par les feuilles de propriétés système.

Si un fichier .vcxproj ne suit pas cette disposition, la build peut générer des résultats inattendus. Par exemple, si vous importez accidentellement une feuille de propriétés système après les feuilles de propriétés définies par l’utilisateur, les paramètres utilisateur sont remplacés par les feuilles de propriétés système.

Même l’expérience au moment du design dans l’IDE dépend dans une certaine mesure de l’ordre des éléments. Par exemple, si votre fichier .vcxproj ne contient pas le groupe d’importations `PropertySheets`, l’IDE peut ne pas être en mesure de déterminer où placer une nouvelle feuille de propriétés créée par l’utilisateur dans le **Gestionnaire de propriétés**. Une feuille d’utilisateur peut alors être remplacée par une feuille système. Bien que l’heuristique utilisée par l’IDE tolère des incohérences mineures dans la disposition du fichier .vcxproj, il est fortement recommandé de ne pas dévier de la structure indiquée plus haut dans cet article.

## <a name="how-the-ide-uses-element-labels"></a>Comment l’IDE utilise les étiquettes d’élément

Dans l’IDE, quand vous définissez la propriété **UseOfAtl** dans la page de propriétés Général, elle est écrite pour le groupe de propriétés Configuration dans le fichier projet, tandis que la propriété **TargetName** dans la même page de propriétés est écrite dans le groupe de propriétés par configuration sans étiquette. Visual Studio examine le fichier XML de la page de propriétés pour obtenir des informations sur les emplacements où il doit écrire chaque propriété. Dans la page de propriétés **Général** de Visual Studio 2019 Enterprise Edition, ce fichier se trouve à l’emplacement suivant : `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Le fichier de règle XML de la page de propriétés définit les informations statiques sur une règle et toutes ses propriétés. Ces informations comprennent notamment la position préférée d’une propriété Rule dans le fichier de destination (le fichier où sa valeur sera écrite). La position préférée est spécifiée par l’attribut Label sur les éléments du fichier projet.

## <a name="property-sheet-layout"></a>Disposition de la feuille de propriétés

L’extrait XML suivant est une disposition minimale d’un fichier de feuille de propriétés (.props). Il est similaire à un fichier .vcxproj, et la fonctionnalité des éléments .props peut être déduite de la discussion précédente.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Pour créer votre propre feuille de propriétés, copiez l’un des fichiers .props dans le dossier VCTargets et modifiez-le selon vos besoins. Dans Visual Studio 2019 Enterprise, le chemin par défaut de VCTargets est le suivant : `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Voir aussi

[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)<br/>
[Fichiers XML de la page de propriétés](property-page-xml-files.md)
