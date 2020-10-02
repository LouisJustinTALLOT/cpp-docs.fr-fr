---
title: Structure des fichiers .vcxproj et .props
description: Comment les fichiers System. vcxproj et. props du projet MSBuild C++ natif stockent les informations de projet.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 562ef0c1b371d7212f31da1917d19c012e4cbb24
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662280"
---
# <a name="vcxproj-and-props-file-structure"></a>`.vcxproj``.props`structure de fichiers et

[MSBuild](../msbuild-visual-cpp.md) est le système de projet par défaut dans Visual Studio. Quand vous choisissez **fichier**  >  **nouveau projet** dans Visual C++ vous créez un projet MSBuild dont les paramètres sont stockés dans un fichier projet XML qui a l’extension *`.vcxproj`* . Le fichier projet peut également importer *`.props`* des fichiers et des *`.targets`* fichiers où les paramètres peuvent être stockés.

Nous vous recommandons de créer et de modifier uniquement *`.vcxproj`* des projets dans l’environnement de développement intégré (IDE) et d’éviter autant que possible les modifications manuelles. Dans la plupart des cas, vous n’avez jamais besoin de modifier manuellement le fichier projet. Dans la mesure du possible, vous devez utiliser les pages de propriétés de Visual Studio pour modifier les paramètres du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

Si vous avez besoin de personnalisations qui ne sont pas possibles dans l’IDE, nous vous recommandons d’ajouter des props ou des cibles personnalisées. Les emplacements pratiques pour insérer des personnalisations sont les *`Directory.Build.props`* *`Directory.Build.targets`* fichiers et, qui sont importés automatiquement dans tous les projets basés sur MSBuild.

Dans certains cas, vous devrez peut-être encore modifier *`.vcxproj`* manuellement un fichier projet ou une feuille de propriétés. Nous vous déconseillons de le modifier manuellement à moins d’avoir une bonne compréhension de MSBuild et de suivre les instructions de cet article. Pour que l’IDE charge et met à jour *`.vcxproj`* automatiquement les fichiers, ces fichiers présentent plusieurs restrictions qui ne s’appliquent pas à d’autres fichiers projet MSBuild. Ils n’ont pas été conçus pour la modification manuelle. Des erreurs peuvent entraîner un blocage de l’IDE ou se comporter de manière inattendue.

Pour les scénarios de modification manuelle, cet article contient des informations de base sur la structure de *`.vcxproj`* et les fichiers associés.

**Important :**

Si vous choisissez de modifier manuellement un *`.vcxproj`* fichier, tenez compte des éléments suivants :

- La structure du fichier doit suivre un formulaire prescrit qui est décrit dans cet article.

- Le système de projet Visual Studio C++ ne prend actuellement pas en charge les caractères génériques ou les listes directement dans les éléments de projet. Par exemple, ces formulaires ne sont pas pris en charge :

   ```xml
   <ItemGroup>
     <None Include="*.txt"/>
     <ClCompile Include="a.cpp;b.cpp"/>
   </ItemGroup>
   ```

   Pour plus d’informations sur la prise en charge des caractères génériques dans les projets et les solutions de contournement possibles, consultez [ `.vcxproj` fichiers et caractères génériques](vcxproj-files-and-wildcards.md).

- Le système de projet Visual Studio C++ ne prend actuellement pas en charge les macros dans les chemins d’accès des éléments de projet. Par exemple, ce formulaire n’est pas pris en charge :

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"/>
   </ItemGroup>
   ```

   « Non pris en charge » signifie qu’il n’est pas garanti que les macros fonctionnent pour toutes les opérations dans l’IDE. Les macros qui ne changent pas leur valeur dans des configurations différentes doivent fonctionner, mais elles peuvent ne pas être conservées si un élément est déplacé vers un autre filtre ou projet. Les macros qui modifient leur valeur pour différentes configurations entraînent des problèmes. Cela est dû au fait que l’IDE ne s’attend pas à ce que les chemins des éléments de projet soient différents pour différentes configurations de projet.

- Pour ajouter, supprimer ou modifier des propriétés de projet correctement lorsque vous les modifiez dans la boîte de dialogue **Propriétés du projet** , le fichier doit contenir des groupes distincts pour chaque configuration de projet. Les conditions doivent être au format suivant :

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

- Chaque propriété doit être spécifiée dans le groupe avec son étiquette correcte, comme spécifié dans le fichier de règles de propriété. Pour plus d’informations, consultez [Fichiers de règles XML des pages de propriétés](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>`.vcxproj` éléments de fichier

Vous pouvez inspecter le contenu d’un *`.vcxproj`* fichier à l’aide de n’importe quel éditeur de texte ou XML. Pour l’afficher dans Visual Studio, cliquez avec le bouton sur le projet dans l’Explorateur de solutions, choisissez **Décharger le projet**, puis **Modifier Foo.vcxproj**.

Vous pouvez tout de suite remarquer que les éléments de niveau supérieur s’affichent dans un ordre particulier. Par exemple :

- La plupart des groupes de propriétés et des groupes de définitions d’éléments se trouvent après l’importation de Microsoft.Cpp.Default.props.

- Toutes les cibles sont importées à la fin du fichier.

- Plusieurs groupes de propriétés, chacun d’eux ayant une étiquette unique, suivent un ordre particulier.

L’ordre des éléments dans le fichier projet est essentiel, car MSBuild est basé sur un modèle d’évaluation séquentielle.  Si votre fichier projet, y compris tous les *`.props`* fichiers et importés *`.targets`* , est constitué de plusieurs définitions d’une propriété, la dernière définition remplace les éléments précédents. Dans l’exemple suivant, la valeur « XYZ » est définie lors de la compilation, car le moteur MSBUild le rencontre en dernier lors de son évaluation.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

L’extrait de code suivant montre un *`.vcxproj`* fichier minimal. Tous les *`.vcxproj`* fichiers générés par Visual Studio contiennent ces éléments MSBuild de niveau supérieur. Elles s’affichent dans cet ordre, bien qu’elles puissent contenir plusieurs copies de chaque élément de niveau supérieur. Les `Label` attributs sont des balises arbitraires qui sont utilisées uniquement par Visual Studio comme des poteaux pour la modification ; ils n’ont aucune autre fonction.

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

Les sections suivantes décrivent l’objectif de chacun de ces éléments et pourquoi ils sont triés de cette façon :

### <a name="project-element"></a>Élément Project

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` est le nœud racine. Il spécifie la version MSBuild à utiliser, ainsi que la cible par défaut à exécuter lorsque ce fichier est passé à MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>Élément ItemGroup ProjectConfigurations

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` contient la description de la configuration du projet. Voici quelques exemples : Debug|Win32, Release|Win32, Debug|ARM, etc. De nombreux paramètres de projet sont spécifiques à une configuration donnée. Par exemple, vous souhaiterez probablement définir des propriétés d’optimisation pour une version Release, mais pas pour une version Debug.

Le `ProjectConfigurations` groupe d’éléments n’est pas utilisé au moment de la génération. L’IDE de Visual Studio requiert le chargement du projet. Ce groupe d’éléments peut être déplacé vers un *`.props`* fichier et importé dans le *`.vcxproj`* fichier. Toutefois, dans ce cas, si vous devez ajouter ou supprimer des configurations, vous devez modifier manuellement le *`.props`* fichier ; vous ne pouvez pas utiliser l’IDE.

### <a name="projectconfiguration-elements"></a>Éléments ProjectConfiguration

L’extrait suivant montre une configuration de projet. Dans cet exemple, « Debug | x64 » est le nom de la configuration. Le nom de la configuration de projet doit être au format `$(Configuration)|$(Platform)` . Un `ProjectConfiguration` nœud peut avoir deux propriétés : `Configuration` et `Platform` . Ces propriétés sont définies automatiquement avec les valeurs spécifiées ici lorsque la configuration est active.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

L’IDE s’attend à trouver une configuration de projet pour toute combinaison `Configuration` de `Platform` valeurs et utilisées dans tous les `ProjectConfiguration` éléments. Souvent, cela signifie qu’un projet peut avoir des configurations de projet incompréhensibles pour satisfaire cette exigence. Par exemple, si un projet a les configurations suivantes :

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

`Globals` contient des paramètres au niveau du projet tels que `ProjectGuid` , `RootNamespace` et `ApplicationType` ou `ApplicationTypeRevision` . Les deux derniers définissent souvent le système d’exploitation cible. Un projet ne peut cibler qu’un seul système d’exploitation, car actuellement, les références et les éléments de projet ne peuvent pas avoir de conditions. Ces propriétés ne sont généralement pas remplacées autre part dans le fichier projet. Ce groupe n’est pas dépendant de la configuration, et il n’y a généralement qu’un seul `Globals` groupe dans le fichier projet.

### <a name="microsoftcppdefaultprops-import-element"></a>Élément Import Microsoft.Cpp.default.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

La feuille de propriétés **Microsoft. cpp. default. props** est fournie avec Visual Studio et ne peut pas être modifiée. Elle contient les paramètres par défaut du projet. Les valeurs par défaut peuvent varier en fonction du type d’application.

### <a name="configuration-propertygroup-elements"></a>Éléments PropertyGroup Configuration

```xml
<PropertyGroup Label="Configuration" />
```

Un groupe de propriétés `Configuration` est attaché à une condition de configuration (comme `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`). Plusieurs copies sont disponibles, une par configuration. Ce groupe de propriétés héberge les propriétés définies pour une configuration spécifique. Les propriétés de configuration, dont PlatformToolset, contrôlent également l’inclusion de feuilles de propriétés système dans **Microsoft.Cpp.props**. Par exemple, si vous définissez la propriété `<CharacterSet>Unicode</CharacterSet>`, la feuille de propriétés système **microsoft.Cpp.unicodesupport.props** est incluse. Si vous Inspectez **Microsoft. cpp. props**, vous verrez la ligne : `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` .

### <a name="microsoftcppprops-import-element"></a>Élément Import Microsoft.Cpp.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

La feuille de propriétés **Microsoft. cpp. props** (directement ou via Imports) définit les valeurs par défaut pour de nombreuses propriétés spécifiques à un outil. Les exemples incluent les propriétés d’optimisation et de niveau d’avertissement du compilateur, la propriété TypeLibraryName de l’outil MIDL, et ainsi de suite. Il importe également différentes feuilles de propriétés système en fonction des propriétés de configuration définies dans le groupe de propriétés immédiatement avant.

### <a name="extensionsettings-importgroup-element"></a>Élément ImportGroup ExtensionSettings

```xml
<ImportGroup Label="ExtensionSettings" />
```

Le groupe `ExtensionSettings` contient les importations des feuilles de propriétés qui font partie des personnalisations de build. Une personnalisation de la build est définie par jusqu’à trois fichiers : un *`.targets`* fichier, un fichier *`.props`* et un *`.xml`* fichier. Ce groupe d’importation contient les importations du *`.props`* fichier.

### <a name="propertysheets-importgroup-elements"></a>Éléments ImportGroup PropertySheets

```xml
<ImportGroup Label="PropertySheets" />
```

Le groupe `PropertySheets` contient les importations des feuilles de propriétés d’utilisateur. Ces importations sont les feuilles de propriétés que vous ajoutez via la vue Gestionnaire de propriétés dans Visual Studio. L’ordre dans lequel ces importations sont répertoriées est important et est reflété dans le Gestionnaire de propriétés. Le fichier projet contient normalement plusieurs instances de ce genre de groupe d’importations, une pour chaque configuration de projet.

### <a name="usermacros-propertygroup-element"></a>Élément PropertyGroup UserMacros

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` contient des propriétés que vous créez comme variables pour personnaliser votre processus de génération. Vous pouvez par exemple définir une macro utilisateur pour définir votre chemin de sortie personnalisé, $(CustomOutputPath), et l’utiliser pour définir d’autres variables. Ce groupe de propriétés héberge de telles propriétés. Dans Visual Studio, ce groupe n’est pas renseigné dans le fichier projet, car Visual C++ ne prend pas en charge les macros utilisateur pour les configurations. Les macros utilisateur sont prises en charge dans les feuilles de propriétés.

### <a name="per-configuration-propertygroup-elements"></a>Éléments PropertyGroup par configuration

```xml
<PropertyGroup />
```

Il existe plusieurs instances de ce groupe de propriétés, une par configuration de projet. Chaque groupe de propriétés doit être attaché à une condition de configuration. Si une configuration est manquante, la boîte de dialogue **Propriétés du projet** ne fonctionne pas correctement. Contrairement aux groupes de propriétés cités précédemment, celui-ci n’a pas d’étiquette. Ce groupe contient des paramètres au niveau de la configuration du projet. Ces paramètres s’appliquent à tous les fichiers qui font partie du groupe d’éléments spécifié. Les métadonnées de définition des éléments de personnalisation de la build sont initialisées ici.

Ce PropertyGroup doit venir après `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` et il ne doit pas y avoir d’autre PropertyGroup sans étiquette avant (sinon, la modification des propriétés du projet ne fonctionnera pas correctement).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Éléments ItemDefinitionGroup par configuration

```xml
<ItemDefinitionGroup />
```

Contient les définitions d’éléments. Ces définitions doivent respecter les mêmes règles que les éléments par configuration sans étiquette `PropertyGroup` .

### <a name="itemgroup-elements"></a>Éléments ItemGroup

```xml
<ItemGroup />
```

`ItemGroup` les éléments contiennent les éléments (fichiers sources, etc.) dans le projet. Les conditions ne sont pas prises en charge pour les éléments de projet (autrement dit, les types d’éléments qui sont traités comme des éléments de projet par définitions de règles).

Les métadonnées doivent avoir des conditions de configuration pour chaque configuration, même si elles sont toutes identiques. Par exemple :

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Le système de projet Visual Studio C++ ne prend actuellement pas en charge les caractères génériques dans les éléments de projet.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Le système de projet Visual Studio C++ ne prend actuellement pas en charge les macros dans les éléments de projet.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Les références, spécifiées dans un ItemGroup, présentent ces limitations :

- Les références ne prennent pas en charge les conditions.

- Les métadonnées de référence ne prennent pas en charge les conditions.

### <a name="microsoftcpptargets-import-element"></a>Élément Import Microsoft.Cpp.targets

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Définit (directement ou via des importations) des cibles C++ telles que la génération, le nettoyage, etc.

### <a name="extensiontargets-importgroup-element"></a>Élément ImportGroup ExtensionTargets

```xml
<ImportGroup Label="ExtensionTargets" />
```

Ce groupe contient des importations pour les fichiers cibles de personnalisation de la build.

## <a name="impact-of-incorrect-ordering"></a>Impact d’un ordre incorrect

L’IDE de Visual Studio dépend du fichier projet dont le classement est décrit précédemment. Par exemple, quand vous définissez une valeur de propriété dans les pages de propriétés, l’IDE place généralement la définition de la propriété dans le groupe de propriétés avec l’étiquette vide. Ce classement garantit que les valeurs par défaut importées dans les feuilles de propriétés système sont remplacées par les valeurs définies par l’utilisateur. De même, les fichiers cibles sont importés à la fin, car ils consomment les propriétés définies précédemment, et puisqu’ils ne définissent généralement pas de propriétés elles-mêmes. De même, les feuilles de propriétés utilisateur sont importées après les feuilles de propriétés système (incluses par *`Microsoft.Cpp.props`* ). Cet ordre permet de s’assurer que l’utilisateur peut remplacer les valeurs par défaut introduites par les feuilles de propriétés système.

Si un *`.vcxproj`* fichier ne respecte pas cette disposition, les résultats de la génération peuvent ne pas être conformes à vos attentes. Par exemple, si vous importez par erreur une feuille de propriétés système après les feuilles de propriétés définies par l’utilisateur, les paramètres utilisateur sont remplacés par les feuilles de propriétés système.

Même l’expérience au moment de la conception de l’IDE dépend d’une certaine précision de l’ordre correct des éléments. Par exemple, si votre *`.vcxproj`* fichier n’a pas le `PropertySheets` groupe d’importation, l’IDE peut ne pas être en mesure de déterminer où placer une nouvelle feuille de propriétés que l’utilisateur a créée dans **Gestionnaire de propriétés**. Cela peut entraîner la substitution d’une feuille de l’utilisateur par une feuille système. Bien que l’heuristique utilisée par l’IDE puisse tolérer des incohérences mineures dans la *`.vcxproj`* disposition des fichiers, nous vous recommandons vivement de ne pas vous écarter de la structure indiquée plus haut dans cet article.

## <a name="how-the-ide-uses-element-labels"></a>Comment l’IDE utilise les étiquettes d’élément

Dans l’IDE, lorsque vous définissez la propriété **UseOfAtl** dans la page de propriétés général, elle est écrite dans le groupe de propriétés de configuration dans le fichier projet. La propriété **TargetName** dans la même page de propriétés est écrite dans le groupe de propriétés par configuration sans étiquette. Visual Studio examine le fichier XML de la page de propriétés pour obtenir des informations sur les emplacements où il doit écrire chaque propriété. Pour la page de propriétés **général** , en supposant que vous disposez d’une version anglaise de Visual Studio 2019 Enterprise Edition, ce fichier est `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` . Le fichier de règle XML de la page de propriétés définit les informations statiques sur une règle et toutes ses propriétés. Ces informations comprennent notamment la position préférée d’une propriété Rule dans le fichier de destination (le fichier où sa valeur sera écrite). La position préférée est spécifiée par l’attribut Label sur les éléments du fichier projet.

## <a name="property-sheet-layout"></a>Disposition de la feuille de propriétés

L’extrait XML suivant est une disposition minimale d’un fichier de feuille de propriétés (.props). Elle est similaire à un *`.vcxproj`* fichier et les fonctionnalités des *`.props`* éléments peuvent être déduites à partir de la discussion précédente.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Pour créer votre propre feuille de propriétés, copiez l’un des *`.props`* fichiers dans le *`VCTargets`* dossier et modifiez-le selon vos besoins. Pour Visual Studio 2019 Enterprise Edition, le *`VCTargets`* chemin d’accès par défaut est `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` .

## <a name="see-also"></a>Voir aussi

[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)\
[Fichiers XML de page de propriétés](property-page-xml-files.md)\
[`.vcxproj` fichiers et caractères génériques](vcxproj-files-and-wildcards.md)
