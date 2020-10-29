---
title: Fichiers de règles XML des pages de propriétés
description: Description du contenu et des fichiers de règles XML de la page de propriétés C++ de l’IDE Visual Studio.
ms.date: 10/14/2020
helpviewer_keywords:
- property page XML files
ms.openlocfilehash: f8aa893fa2b062da2f1d0784e5a9b1a6f2b30c95
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921397"
---
# <a name="property-page-xml-rule-files"></a>Fichiers de règles XML des pages de propriétés

Les pages de propriétés du projet dans l’IDE sont configurées par des fichiers XML dans le dossier des règles par défaut. Les fichiers XML décrivent les noms des règles, les catégories et les propriétés individuelles, leur type de données, leurs valeurs par défaut et comment les afficher. Quand vous définissez une propriété dans l’IDE, la nouvelle valeur est stockée dans le fichier projet.

::: moniker range="msvc-140"

Le chemin d’accès au dossier des règles par défaut dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier règles est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* . La `<version>` valeur est *`v140`* dans Visual Studio 2015. `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2015 Community Edition en anglais peut être *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* .

::: moniker-end

::: moniker range="msvc-150"

Le chemin d’accès au dossier des règles par défaut dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2017, le dossier règles est *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier Rules est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* , où la `<version>` valeur se trouve *`v140`* dans Visual Studio 2015. Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2017 Community Edition en anglais peut être *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* .

::: moniker-end

::: moniker range=">=msvc-160"

Le chemin d’accès au dossier des règles par défaut dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2019 ou version ultérieure, le dossier règles est *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* , où la `<version>` valeur se trouve *`v160`* dans Visual Studio 2019. `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Dans Visual Studio 2017, le dossier Rules est *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier règles est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* . Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2019 Community Edition en anglais peut être *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* .

::: moniker-end

Il vous suffit de comprendre le fonctionnement interne de ces fichiers et de l’IDE de Visual Studio dans deux scénarios :

- Vous souhaitez créer une page de propriétés personnalisée, ou
- Vous souhaitez personnaliser les propriétés de votre projet sans utiliser l’IDE de Visual Studio.

## <a name="contents-of-rule-files"></a>Contenu des fichiers de règles

Tout d’abord, nous allons ouvrir les pages de propriétés d’un projet. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** , puis choisissez **Propriétés** :

![Affiche la boîte de dialogue des propriétés du projet C++ Visual Studio](../media/cpp-property-page-2017.png)

Chaque nœud sous **Propriétés de configuration** est appelé *règle* . Une règle représente parfois un outil unique tel que le compilateur. En général, le terme fait référence à un qui a des propriétés, qui s’exécute et qui peut produire une sortie. Chaque règle est renseignée à partir d’un fichier XML dans le dossier des règles par défaut. Par exemple, la règle C/C++ qui est indiquée ici est remplie par *« cl.xml »* .

Chaque règle possède un ensemble de propriétés, qui sont organisées en *catégories* . Chaque sous-nœud sous une règle représente une catégorie. Par exemple, le nœud **optimisation** sous **C/C++** contient toutes les propriétés relatives à l’optimisation de l’outil compilateur. Les propriétés et leurs valeurs sont rendues dans un format de grille dans le volet droit.

Vous pouvez ouvrir *`cl.xml`* dans le bloc-notes ou dans n’importe quel éditeur XML. Vous verrez un nœud racine appelé `Rule` . Elle définit la même liste de propriétés qui s’affichent dans l’interface utilisateur, ainsi que des métadonnées supplémentaires.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
  <!-- . . . -->
</Rule>
```

Il y a un fichier XML pour chaque nœud sous **Propriétés de configuration** dans l’interface utilisateur des pages de propriétés. Vous pouvez ajouter ou supprimer des règles dans l’interface utilisateur : en incluant ou en supprimant des emplacements aux fichiers XML correspondants dans le projet. Par exemple, il s’agit de savoir comment *`Microsoft.CppBuild.targets`* (trouvé un niveau supérieur au dossier 1033) *`cl.xml`* :

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Si vous supprimez *`cl.xml`* toutes les données, vous disposez de cette infrastructure de base :

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
    <!-- . . . -->
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

La section suivante décrit chaque élément principal et certaines des métadonnées que vous pouvez attacher.

### <a name="rule-attributes"></a>Attributs de règle

Un **`<Rule>`** élément est le nœud racine dans le fichier XML. Il peut avoir de nombreux attributs :

```xml
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```

- **`Name`** : L’attribut Name est un ID pour le `Rule` . Elle doit être unique parmi tous les fichiers XML de page de propriétés pour un projet.

- **`PageTemplate`** : La valeur de cet attribut est utilisée par l’interface utilisateur pour faire un choix dans une collection de modèles d’interface utilisateur. Le modèle « tool » montre les propriétés selon un format de grille standard. D’autres valeurs prédéfinies de cet attribut sont « debugger » et « generic ». Regardez respectivement le nœud Debugging et le nœud General pour voir le format d’interface utilisateur qui résulte de la spécification de ces valeurs. L’interface utilisateur pour le modèle de page « débogueur » utilise une zone de liste déroulante pour basculer entre les propriétés de différents débogueurs. Le modèle « générique » affiche des catégories de propriétés différentes dans une page, par opposition à l’utilisation de plusieurs sous-nœuds de catégorie sous le `Rule` nœud. Cet attribut n’est qu’une suggestion de l’interface utilisateur. Le fichier XML est conçu pour être indépendant de l’interface utilisateur. Une autre interface utilisateur peut utiliser cet attribut à des fins différentes.

- **`SwitchPrefix`** : Le préfixe utilisé dans la ligne de commande pour les commutateurs. Si la valeur `"/"` est, les commutateurs ressemblent à,, **`/ZI`** **`/nologo`** **`/W3`** , et ainsi de suite.

- **`Order`** : Suggestion d’un client d’interface utilisateur potentiel sur l’emplacement relatif de ce `Rule` par rapport à toutes les autres règles du système.

- **`xmlns`** : Élément XML standard. Vous pouvez voir trois espaces de noms répertoriés. Ces attributs correspondent respectivement aux espaces de noms des classes de désérialisation XML, du schéma XML et de l’espace de noms System.

- **`DisplayName`** : Nom affiché dans l’interface utilisateur de la page de propriétés pour le `Rule` nœud. Cette valeur est localisée. Nous avons créé `DisplayName` comme élément enfant de `Rule` plutôt que comme attribut (comme `Name` ou) en `SwitchPrefix` raison des exigences de l’outil de localisation interne. D’un point de vue XML, les deux sont équivalents. Vous pouvez donc simplement en faire un attribut pour réduire l’encombrement ou le laisser tel quel.

- **`DataSource`** : Cette propriété importante indique au système de projet l’emplacement où lire et écrire la valeur de la propriété, ainsi que son regroupement (expliqué plus tard). Pour *`cl.xml`* , ces valeurs sont les suivantes :

    ```xml
    <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
    ```

  - `Persistence="ProjectFile"` indique au système de projet que toutes les propriétés de l' `Rule` élément doivent être écrites dans le fichier projet ou dans le fichier de feuille de propriétés (en fonction du nœud utilisé pour générer les pages de propriétés). L’autre valeur possible est `"UserFile"` , qui écrira la valeur dans le *`.user`* fichier.

  - `ItemType="ClCompile"` indique que les propriétés seront stockées en tant que métadonnées ItemDefinition ou que métadonnées d’élément (ces dernières seulement si les pages de propriétés ont été générées à partir d’un nœud de fichier dans l’Explorateur de solutions) de ce type d’élément. Si ce champ n’est pas défini, la propriété est écrite sous la forme d’une propriété commune dans PropertyGroup.

  - `Label=""` indique que quand les propriétés sont écrites en tant que métadonnées `ItemDefinition`, l’étiquette de l’élément ItemDefinitionGroup parent est vide (tous les éléments MSBuild peuvent avoir une étiquette). Visual Studio 2017 et les versions ultérieures utilisent des groupes étiquetés pour naviguer dans le fichier projet .vcxproj. Les groupes qui contiennent la plupart des `Rule` propriétés ont une chaîne vide en tant qu’étiquette.

  - `HasConfigurationCondition="true"` indique au système de projet d’ajouter une condition de configuration à la valeur pour qu’elle s’applique uniquement à la configuration de projet actuelle (la condition peut être appliquée au groupe parent ou à la valeur elle-même). Par exemple, ouvrez les pages de propriétés du nœud du projet et définissez la valeur de la propriété **Considérer les avertissements comme des erreurs** sous **Propriétés de configuration > Générales C/C++** sur « Oui ». La valeur suivante est écrite dans le fichier projet. Notez la condition de configuration associée à l’élément ItemDefinitionGroup parent.

    ```xml
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
      <ClCompile>
        <TreatWarningAsError>true</TreatWarningAsError>
      </ClCompile>
    </ItemDefinitionGroup>
    ```

     Si cette valeur est définie dans la page de propriétés d’un fichier spécifique, par exemple *`stdafx.cpp`* , la valeur de la propriété doit être écrite sous l' `stdafx.cpp` élément dans le fichier projet, comme indiqué ici. Notez que la condition de configuration est directement attachée aux métadonnées elles-mêmes :

    ```xml
    <ItemGroup>
      <ClCompile Include="stdafx.cpp">
        <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
      </ClCompile>
    </ItemGroup>
    ```

  Un autre attribut de `DataSource` non répertorié ici est `PersistedName` . Vous pouvez utiliser cet attribut pour représenter une propriété dans le fichier projet en utilisant un nom différent. Par défaut, cet attribut est défini sur le de la propriété `Name` .

  Une propriété individuelle peut substituer le `DataSource` de son parent `Rule` . Dans ce cas, l’emplacement de la valeur de cette propriété sera différent des autres propriétés de `Rule` .

- D’autres attributs d’un `Rule` , y compris `Description` et `SupportsFileBatching` , ne sont pas indiqués ici. Vous pouvez obtenir l’ensemble complet des attributs applicables à un `Rule` ou à tout autre élément en parcourant la documentation de ces types. Vous pouvez aussi examiner les propriétés publiques sur les types dans l’espace de noms `Microsoft.Build.Framework.XamlTypes` de l’assembly `Microsoft.Build.Framework.dll`.

- **`DisplayName`** , **`PageTemplate`** et **`Order`** sont des propriétés liées à l’interface utilisateur qui sont présentes dans ce modèle de données indépendant de l’interface utilisateur. Ces propriétés sont généralement utilisées par les interfaces utilisateur utilisées pour afficher les pages de propriétés. `DisplayName` et `Description` sont deux propriétés qui sont présentes sur presque tous les éléments du fichier XML. Et, ces deux propriétés sont les seules à être localisées.

### <a name="category-elements"></a>Éléments category

Un `Rule` peut avoir plusieurs `Category` éléments. L’ordre dans lequel les catégories sont répertoriées dans le fichier XML est une suggestion de l’interface utilisateur qui permet d’afficher les catégories dans le même ordre. Par exemple, l’ordre des catégories sous le nœud **C/C++** que vous voyez dans l’interface utilisateur est le même que l’ordre dans *`cl.xml`* . Voici un exemple de catégorie :

```xml
<Category Name="Optimization">
  <Category.DisplayName>
    <sys:String>Optimization</sys:String>
  </Category.DisplayName>
</Category>
```

Cet extrait de code montre les `Name` `DisplayName` attributs et qui ont été décrits précédemment. Là encore, il existe d’autres attributs `Category` que peut avoir qui ne sont pas affichés dans l’exemple. Vous pouvez en savoir plus à leur sujet en lisant la documentation ou en examinant les assemblys à l’aide de *`ildasm.exe`* .

### <a name="property-elements"></a>Éléments de propriété

La plupart du fichier de règles se compose d' `Property` éléments. Ils contiennent la liste de toutes les propriétés dans un `Rule` . Chaque propriété peut être l’un des cinq types possibles présentés dans l’infrastructure de base : `BoolProperty` , `EnumProperty` ,, `IntProperty` `StringProperty` et `StringListProperty` . Vous n’avez peut-être que quelques-uns de ces types dans votre fichier. Une propriété a plusieurs attributs qui lui permettent d’être décrits en détail. `StringProperty`Est décrit ici. Les autres sont similaires.

```xml
<StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
  <StringProperty.DisplayName>
    <sys:String>Object File Name</sys:String>
  </StringProperty.DisplayName>
  <StringProperty.Description>
    <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
  </StringProperty.Description>
</StringProperty>
```

La plupart des attributs de l’extrait de code ont été décrits précédemment. Les nouveaux sont `Subtype` , `Category` et `Switch` .

- **`Subtype`** est un attribut disponible uniquement pour `StringProperty` les `StringListProperty` éléments et. Il fournit des informations contextuelles. Par exemple, la valeur `file` indique que la propriété représente un chemin d’accès de fichier. Visual Studio utilise ces informations contextuelles pour améliorer l’expérience de modification. Par exemple, elle peut fournir une fenêtre de l’Explorateur Windows qui permet à l’utilisateur de choisir le fichier visuellement comme éditeur de la propriété.

- **`Category`** : Catégorie sous laquelle cette propriété se trouve. Recherchez cette propriété sous la catégorie **Fichiers de sortie** dans l’interface utilisateur.

- **`Switch`** : Lorsqu’une règle représente un outil tel que l’outil compilateur, la plupart des `Rule` propriétés sont passées en tant que commutateurs à l’exécutable de l’outil au moment de la génération. La valeur de cet attribut indique le littéral de commutateur à utiliser. L' `<StringProperty>` exemple spécifie que son commutateur doit être **`Fo`** . Associé à l' `SwitchPrefix` attribut sur le parent `Rule` , cette propriété est passée au fichier exécutable en tant que  **`/Fo"Debug\"`** . Elle est visible dans la ligne de commande pour C/C++ dans l’interface utilisateur de la page de propriétés.

   Voici d’autres attributs de propriété :

- **`Visible`** : Si vous ne souhaitez pas que votre propriété apparaisse dans les pages de propriétés, mais que vous souhaitez qu’elle soit disponible au moment de la génération, affectez à cet attribut la valeur `false` .

- **`ReadOnly`** : Si vous souhaitez fournir une vue en lecture seule de la valeur de cette propriété dans les pages de propriétés, affectez à cet attribut la valeur `true` .

- **`IncludeInCommandLine`** : Au moment de la génération, un outil peut ne pas avoir besoin de certaines de ses propriétés. Affectez à cet attribut la valeur `false` pour empêcher la transmission d’une propriété particulière.
