---
title: Fichiers de règles XML des pages de propriétés
ms.date: 04/27/2017
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 7c2ce82cf13b9999102c5ac6df42ccb601e4e729
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467234"
---
# <a name="property-page-xml-rule-files"></a>Fichiers de règles XML des pages de propriétés

Les pages de propriétés de projet dans l’IDE sont configurées par des fichiers XML du dossier VCTargets. Le chemin exact varie selon la ou les éditions de Visual Studio installées et la langue du produit. Pour Visual Studio 2017 Enterprise Edition, en anglais, le chemin est `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Les fichiers XML décrivent les noms des règles, les catégories et les propriétés individuelles, leur type de données, leur valeur par défaut et comment elles doivent être affichées. Quand vous définissez une propriété dans l’IDE, la nouvelle valeur est stockée dans le fichier projet.

Les seuls scénarios dans lesquels vous devez comprendre que le fonctionnement interne de ces fichiers et de l’IDE Visual Studio sont (a) vous voulez créer une page de propriétés personnalisées ou (b) vous voulez personnaliser les propriétés de votre projet par un moyen autre que via l’IDE Visual Studio.

Nous allons d’abord ouvrir les pages de propriétés pour un projet (cliquez avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions** et choisissez Propriétés) :

![Propriétés de projet Visual C++](media/cpp-property-page-2017.png)

Chaque nœud sous **Propriétés de configuration** est appelé une règle. Une règle représente parfois un seul outil comme le compilateur, mais en général, le terme fait référence à un élément qui a des propriétés, qui s’exécute et qui peut produire une sortie. Chaque règle est constituée à partir d’un fichier XML dans le dossier VCTargets. Par exemple, la règle C/C++ qui est montrée ci-dessus est constituée à partir de « cl.xml ».

Comme indiqué ci-dessus, chaque règle a un jeu de propriétés qui sont organisées en catégories. Chaque sous-nœud sous une règle représente une catégorie. Par exemple, le nœud Optimisation sous C/C++ contient toutes les propriétés de l’outil compilateur relatives à l’optimisation. Les propriétés et leurs valeurs sont montrées selon un format de grille dans le volet droit.

Vous pouvez ouvrir cl.xml dans le Bloc-notes ou dans n’importe quel éditeur XML (voir la capture ci-dessous). Vous voyez un nœud racine appelé Rule, sous lequel se trouve la même liste de propriétés définies que celle affichée dans l’interface utilisateur, ainsi que des métadonnées supplémentaires.

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
...
```

Un fichier XML correspond à chaque nœud sous Propriétés de configuration dans l’interface utilisateur des pages de propriétés. Vous pouvez ajouter ou supprimer des règles dans l’interface utilisateur en incluant ou en supprimant les emplacements de fichiers XML correspondants dans le projet. Par exemple, voici comment Microsoft.CppBuild.targets (un niveau au-dessus du dossier 1033) inclut cl.xml :

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Si vous supprimez toutes les données de cl.xml, vous obtenez au final la structure suivante :

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

La section suivante décrit les principaux éléments et certaines des métadonnées qui peuvent y être attachées.

1. **Rule :**  Rule est généralement le nœud racine dans le fichier XML ; il peut avoir de nombreux attributs :

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Name :** l’attribut Name est un ID pour la règle. Il doit être unique parmi tous les fichiers XML des pages de propriétés pour un projet.

   b. **PageTemplate :** la valeur de cet attribut est utilisée par l’interface utilisateur pour choisir dans une collection de modèles d’interface utilisateur. Le modèle « tool » montre les propriétés selon un format de grille standard. D’autres valeurs prédéfinies de cet attribut sont « debugger » et « generic ». Regardez respectivement le nœud Debugging et le nœud General pour voir le format d’interface utilisateur qui résulte de la spécification de ces valeurs. L’interface utilisateur pour le modèle de page « debugger » utilise une zone de liste déroulante pour basculer entre les propriétés des différents débogueurs, tandis que le modèle « generic » affiche les différentes catégories de propriétés dans une même page, au lieu d’avoir plusieurs sous-nœuds de catégorie sous le nœud Rule. Cet attribut est simplement une suggestion pour l’interface utilisateur ; le fichier XML est conçu pour être indépendant de l’interface utilisateur. Une autre interface utilisateur peut utiliser cet attribut à des fins différentes.

   c. **SwitchPrefix :** il s’agit du préfixe utilisé dans la ligne de commande pour les commutateurs. La valeur « / » aboutirait à des commutateurs comme /ZI, /nologo, /W3, etc.

   d. **Order :** il s’agit d’une suggestion à un client d’interface utilisateur potentiel quant à l’emplacement relatif de cette règle par rapport à toutes les autres règles du système.

   e. **xmlns :** il s’agit d’un élément XAML standard. Vous pouvez voir trois espaces de noms répertoriés. Ils correspondent aux espaces de noms pour les classes de désérialisation XAML, pour le schéma XAML et pour l’espace de noms système, respectivement.

   f. **DisplayName :** il s’agit du nom qui s’affiche sur l’interface utilisateur des pages de propriétés pour le nœud Rule. Cette valeur est localisée. Nous avons créé DisplayName en tant qu’élément enfant de Rule et non pas comme attribut (comme Name ou SwitchPrefix) en raison des nécessités de l’outil de localisation interne. Du point de vue du XAML, les deux sont équivalents. Vous pouvez donc simplement en faire un attribut pour réduire l’encombrement ou le laisser tel quel.

   g. **DataSource :** il s’agit d’une propriété très importante qui indique au système de projet l’emplacement où la valeur de la propriété doit être lue et écrite, ainsi que son regroupement (voir ci-dessous). Pour cl.xml, ces valeurs sont :

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` indique au système de projet que toutes les propriétés de la règle doivent être écrites dans le fichier projet ou dans le fichier de feuille de propriétés (selon le nœud qui a été utilisé pour générer les pages de propriétés). L’autre valeur possible est « UserFile » : la valeur est alors écrite dans le fichier .user.

   - `ItemType="ClCompile"` indique que les propriétés seront stockées en tant que métadonnées ItemDefinition ou que métadonnées d’élément (ces dernières seulement si les pages de propriétés ont été générées à partir d’un nœud de fichier dans l’Explorateur de solutions) de ce type d’élément. Si ce champ n’est pas défini, la propriété est écrite comme propriété commune dans un élément PropertyGroup.

   - `Label=""` indique que quand les propriétés sont écrites en tant que métadonnées `ItemDefinition`, l’étiquette de l’élément ItemDefinitionGroup parent est vide (tous les éléments MSBuild peuvent avoir une étiquette). Visual Studio 2017 utilise des groupes étiquetés pour naviguer dans le fichier projet .vcxproj. Notez que les groupes qui contiennent la plupart des propriétés de Rule ont une chaîne vide comme étiquette.

   - `HasConfigurationCondition="true"` indique au système de projet d’ajouter une condition de configuration à la valeur pour qu’elle s’applique uniquement à la configuration de projet actuelle (la condition peut être appliquée au groupe parent ou à la valeur elle-même). Par exemple, ouvrez les pages de propriétés du nœud du projet et définissez la valeur de la propriété **Considérer les avertissements comme des erreurs** sous **Propriétés de configuration > Générales C/C++** sur « Oui ». La valeur suivante est écrite dans le fichier projet. Notez la condition de configuration associée à l’élément ItemDefinitionGroup parent.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Si cette valeur était définie dans la page de propriétés pour un fichier spécifique, comme stdafx.cpp, la valeur de la propriété serait écrite sous l’élément stdafx.cpp dans le fichier de projet, comme indiqué ci-dessous. Notez comment la condition de configuration est directement attachée aux métadonnées elles-mêmes.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Un autre attribut de **DataSource** non répertoriée ci-dessus est **PersistedName**. Vous pouvez utiliser cet attribut pour représenter une propriété dans le fichier projet en utilisant un nom différent. Par défaut, cet attribut est défini sur la valeur **Name** de la propriété.

   Une propriété individuelle peut remplacer la source de données de sa règle parent. Dans ce cas, l’emplacement de la valeur de cette propriété est différent des autres propriétés de la règle.

   h. Il existe des autres attributs d’une règle, comme Description, SupportsFileBatching, etc., qui ne sont pas affichés ici. Vous pouvez obtenir l’ensemble complet des attributs applicables à une règle ou sur n’importe quel autre élément en parcourant la documentation pour ces types. Vous pouvez aussi examiner les propriétés publiques sur les types dans l’espace de noms `Microsoft.Build.Framework.XamlTypes` de l’assembly `Microsoft.Build.Framework .dll`.

   i. **DisplayName**, **PageTemplate** et **Order** sont des propriétés relatives à l’interface utilisateur qui sont présentes dans ce modèle de données indépendant de l’interface utilisateur. Ces propriétés sont généralement utilisées par les interfaces utilisateur utilisées pour afficher les pages de propriétés. **DisplayName** et **Description** sont deux propriétés présentes sur presque tous les éléments du fichier XML. Il s’agit des deux seules propriétés qui sont localisées (la localisation de ces chaînes est expliquée dans un billet ultérieur).

1. **Category :** une règle peut avoir plusieurs catégories. L’ordre dans lequel les catégories sont répertoriées dans le fichier XML est une suggestion faite à l’interface utilisateur d’afficher les catégories dans le même ordre. Par exemple, l’ordre des catégories sous le nœud C/C++ tel qu’il est vu dans l’interface utilisateur – Général, Optimisation, Préprocesseur,...  – est le même que celui de cl.xml. Voici un exemple de catégorie :

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   L’extrait de code ci-dessus montre les attributs **Name** et **DisplayName** qui ont été décrits précédemment. À nouveau, une **catégorie** peut avoir d’autres attributs qui ne sont pas utilisés ci-dessus. Vous pouvez trouver des informations sur ceux-ci en lisant la documentation ou en examinant les assemblys avec ildasm.exe.

1. **Properties :** il s’agit de l’essentiel du fichier XML. Cette section contient la liste de toutes les propriétés de cette règle. Chaque propriété peut être d’un des cinq types possibles indiqués dans le squelette XAML ci-dessus. Bien sûr, seuls quelques-uns de ces types peuvent être présents dans votre fichier. Une propriété a plusieurs attributs qui lui permettent d’être décrite de façon détaillée. J’explique ici seulement l’attribut **StringProperty**. Les autres sont très similaires.

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

   La plupart des attributs de l’extrait de code ont été décrits précédemment. Les nouveaux attributs sont Subtype, Category et Switch.

   a. **Subtype** est un attribut disponible seulement pour **StringProperty** et **StringListProperty** ; il donne des informations contextuelles. Par exemple, la valeur « file » indique que la propriété représente un chemin de fichier. Ces informations contextuelles sont utilisées pour améliorer l’expérience d’édition en fournissant un Explorateur Windows comme éditeur de la propriété qui permet à l’utilisateur de choisir le fichier visuellement.

   b. **Category :** ceci déclare la catégorie sous laquelle cette propriété se trouve. Recherchez cette propriété sous la catégorie **Fichiers de sortie** dans l’interface utilisateur.

   c. **Switch :** quand une règle représente un outil, comme l’outil compilateur dans ce cas, la plupart des propriétés de la règle sont passées en tant que commutateurs à l’exécutable de l’outil lors de la build. La valeur de cet attribut indique le littéral du commutateur à utiliser. La propriété ci-dessus spécifie que son commutateur doit être **Fo**. Combinée avec l’attribut **SwitchPrefix** sur la règle parent, cette propriété est passée à l’exécutable en tant que **/Fo"Debug\"** (visible dans la ligne de commande pour C/C++ dans l’interface utilisateur de la page des propriétés).

   Voici d’autres attributs de propriété :

   d. **Visible :** si, pour une raison quelconque, vous ne voulez pas que votre propriété apparaisse dans les pages de propriétés (mais probablement qu’elle reste néanmoins disponible lors de la génération), définissez cet attribut sur false.

   e. **ReadOnly :** si vous voulez fournir une vue en lecture seule de la valeur de cette propriété dans les pages de propriétés, définissez cet attribut sur true.

   f. **IncludeInCommandLine :** certaines propriétés n’ont pas besoin d’être passées à un outil lors de la génération. Définissez cet attribut sur false pour qu’elles ne soient pas passées.
