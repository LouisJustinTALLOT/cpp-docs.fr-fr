---
title: Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
ms.date: 07/27/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: f9876a2ce164d0a129ba21405ec61fdcbbd8de91
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507476"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Utiliser des ensembles de règles pour spécifier les règles C++ à exécuter

Dans Visual Studio, vous pouvez créer et modifier un *ensemble de règles* personnalisé pour répondre à des besoins de projet spécifiques associés à l’analyse du code. Les ensembles de règles par défaut sont stockés dans *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

**Visual Studio 2017 version 15,7 et versions ultérieures :** Vous pouvez créer des ensembles de règles personnalisés à l’aide de n’importe quel éditeur de texte et les appliquer dans les builds de ligne de commande, quel que soit le système de génération que vous utilisez. Pour plus d’informations, consultez [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md).

Pour créer un ensemble de règles C++ personnalisé dans Visual Studio, un projet C/C++ doit être ouvert dans l’IDE de Visual Studio. Vous ouvrez ensuite un ensemble de règles standard dans l’éditeur d’ensembles de règles, puis vous ajoutez ou supprimez des règles spécifiques et, éventuellement, vous modifiez l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.

Pour créer un ensemble de règles personnalisé, enregistrez-le à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant

::: moniker range="<=vs-2017"

1. Dans Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sélectionnez la page **Propriétés de configuration** général de l' > **analyse du code** > **General** .

1. Dans la liste déroulante **ensemble de règles** , effectuez l’une des opérations suivantes :

   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Choisissez **\<Browse...>** de spécifier un ensemble de règles existant qui ne figure pas dans la liste.

1. Choisissez **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.

::: moniker-end
::: moniker range=">=vs-2019"

1. Dans Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sélectionnez la page **Propriétés de configuration** > **analyse du code** > **Microsoft** .

1. Dans la liste déroulante **règles actives** , effectuez l’une des opérations suivantes :

   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Choisissez **\<Browse...>** de spécifier un ensemble de règles existant qui ne figure pas dans la liste.

1. Choisissez **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.

::: moniker-end

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier un ensemble de règles dans l’éditeur d’ensembles de règles

- Pour modifier le nom complet de l’ensemble de règles, dans le menu **affichage** , choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans la zone **nom** . Notez que le nom d’affichage peut être différent du nom de fichier.

- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.

- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, activez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.

- Pour modifier l’action entreprise lorsqu’une règle est violée dans une analyse du code, choisissez le champ **action** pour la règle, puis choisissez l’une des valeurs suivantes :

     **Avertissement** : génère un avertissement.

     **Erreur** : génère une erreur.

     **Info** -génère un message.

     **None** : désactive la règle. Cette action revient à supprimer la règle de l’ensemble de règles.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs de l’éditeur d’ensembles de règles à l’aide de la barre d’outils Éditeur d’ensemble de règles

- Pour développer les règles de tous les groupes, choisissez **développer tout**.

- Pour réduire les règles de tous les groupes, choisissez **réduire tout**.

- Pour modifier le champ par lequel les règles sont regroupées, choisissez le champ dans la liste **regrouper par** . Pour afficher les règles non groupées, choisissez **\<None>** .

- Pour ajouter ou supprimer des champs dans les colonnes de règles, choisissez **options de colonne**.

- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **Masquer les règles qui ne s’appliquent pas à la solution actuelle**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action **aucun** , choisissez **afficher les règles qui ne sont pas activées**.

- Pour ajouter ou supprimer des ensembles de règles par défaut Microsoft pour l’ensemble de règles actuel, choisissez **Ajouter ou supprimer des ensembles de règles enfants**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Pour créer un ensemble de règles dans un éditeur de texte

Vous pouvez créer un ensemble de règles personnalisé dans un éditeur de texte, le stocker dans n’importe quel emplacement avec une *`.ruleset`* extension et l’appliquer à l’aide de l' [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) option du compilateur.

L’exemple suivant montre un fichier d’ensemble de règles de base que vous pouvez utiliser comme point de départ :

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="10.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

## <a name="ruleset-schema"></a>Schéma de l’ensemble de règles

Le schéma RuleSet suivant décrit le schéma XML d’un fichier RuleSet. Le schéma de l’ensemble de règles est stocké dans *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Schemas\RuleSet.xsd`* . Vous pouvez l’utiliser pour créer vos propres RuleSet par programme ou pour valider si vos ensembles de règles personnalisés respectent le format correct. Pour plus d’informations, consultez [Comment : créer un document XML basé sur un schéma XSD](/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema).

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:annotation>
    <xs:documentation xml:lang="en">
            Visual Studio Code Analysis Rule Set Schema Definition Language.
            Copyright (c) Microsoft Corporation. All rights reserved.
        </xs:documentation>
  </xs:annotation>

  <!-- Every time this file changes, be sure to change the Validate method for the corresponding object in the code -->

  <xs:element name="RuleSet" type="TRuleSet">
  </xs:element>

  <xs:complexType name="TLocalization">
    <xs:all>
      <xs:element name="Name" type="TName" minOccurs="0" maxOccurs="1" />
      <xs:element name="Description" type="TDescription" minOccurs="0" maxOccurs="1" />
    </xs:all>
    <xs:attribute name="ResourceAssembly" type="TNonEmptyString" use="required" />
    <xs:attribute name="ResourceBaseName" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleHintPaths">
    <xs:sequence>
      <xs:element name="Path" type="TNonEmptyString" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="TName">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TDescription">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TInclude">
    <xs:attribute name="Path" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TIncludeAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TIncludeAll">
    <xs:attribute name="Action" type="TIncludeAllAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRule">
    <xs:attribute name="Id" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TRuleAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRules">
    <xs:sequence>
      <xs:element name="Rule" type="TRule" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="AnalyzerId" type="TNonEmptyString" use="required" />
    <xs:attribute name="RuleNamespace" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleSet">
    <xs:sequence minOccurs="0" maxOccurs="1">
      <xs:element name="Localization" type="TLocalization" minOccurs="0" maxOccurs="1" />
      <xs:element name="RuleHintPaths" type="TRuleHintPaths" minOccurs="0" maxOccurs="1" />
      <xs:element name="IncludeAll" type="TIncludeAll" minOccurs="0" maxOccurs="1" />
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Include" type="TInclude" minOccurs="0" maxOccurs="unbounded" />
        <xs:element name="Rules" type="TRules" minOccurs="0" maxOccurs="unbounded">
          <xs:unique name="UniqueRuleName">
            <xs:selector xpath="Rule" />
            <xs:field xpath="@Id" />
          </xs:unique>
        </xs:element>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="Name" type="TNonEmptyString" use="required" />
    <xs:attribute name="Description" type="xs:string" use="optional" />
    <xs:attribute name="ToolsVersion" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:simpleType name="TRuleAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
      <xs:enumeration value="Default"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAllAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TNonEmptyString">
    <xs:restriction base="xs:string">
      <xs:minLength value="1" />
    </xs:restriction>
  </xs:simpleType>
  
</xs:schema>

```

Détails de l’élément de schéma :

| Schema (élément) | Description |
|--------------------|--------------|
| `TLocalization` | Informations de localisation, y compris le nom du fichier RuleSet, la description du fichier RuleSet, le nom de l’assembly de ressources contenant la ressource localisée et le nom de base de la ressource localisée |
| `TRuleHintPaths` | Chemins d’accès aux fichiers utilisés comme indications pour rechercher des fichiers RuleSet |
| `TName` | Nom du fichier RuleSet actuel |
| `TDescription` | Description du fichier RuleSet actuel |
| `TInclude` | Chemin d’un ensemble de règles inclus avec une action de règle |
| `TIncludeAll` | Action de règle pour toutes les règles |
| `TRule` | ID de règle avec action de règle |
| `TRules` | Collection d’une ou plusieurs règles |
| `TRuleSet` | Le format de fichier RuleSet constitué d’informations de localisation, de chemins d’accès aux indicateurs de règles, inclut toutes les informations, inclut des informations, des informations sur les règles, un nom, une description et des informations sur la version des outils |
| `TRuleAction` | Énumération décrivant une action de règle, telle qu’une erreur, un avertissement, une info, un élément masqué ou aucun |
| `TIncludeAction` | Énumération décrivant une action de règle telle qu’une erreur, un avertissement, une info, masqué, aucun ou par défaut |
| `TIncludeAllAction` | Énumération décrivant une action de règle telle qu’une erreur, un avertissement, une info ou un masqué |

Pour voir un exemple d’ensemble de règles, consultez [pour créer un ensemble de règles dans un éditeur de texte](#to-create-a-rule-set-in-a-text-editor)ou l’un des ensembles de règles par défaut stockés dans `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` .
