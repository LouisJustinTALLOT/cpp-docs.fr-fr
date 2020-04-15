---
title: Macros pour les modèles du fournisseur OLE DB
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369807"
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros pour les modèles du fournisseur OLE DB

Les macros OLE DB Templates Provider offrent des fonctionnalités dans les catégories suivantes :

## <a name="property-set-map-macros"></a>Macros de carte de jeu de propriété

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Marque le début d’un ensemble de propriétés.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Marque le début d’un ensemble de propriétés.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Marque le début d’un ensemble de propriété qui peut être caché ou défini en dehors de la portée du fournisseur.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Chaînes de groupes immobiliers ensemble.|
|[END_PROPERTY_SET](#end_property_set)|Marque la fin d’un ensemble de propriétés.|
|[END_PROPSET_MAP](#end_propset_map)|Marque la fin d’une carte de propriété définie.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Définit une propriété spécifique dans une propriété définie à une valeur par défaut.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Définit une propriété spécifique dans une propriété définie à une valeur fournie par vous. Vous permet également de définir des drapeaux et des options.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Définit une propriété spécifique dans une propriété définie à une valeur fournie par vous.|

## <a name="column-map-macros"></a>Macros de carte de colonne

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Marque le début des entrées de carte de colonne fournisseur.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Marque la fin des entrées de carte de colonne du fournisseur.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Représente une colonne spécifique prise en charge par le fournisseur.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Représente une colonne spécifique prise en charge par le fournisseur. Vous pouvez spécifier le type de données de colonne.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Représente une colonne spécifique prise en charge par le fournisseur. Vous pouvez spécifier la taille, le type de données, la précision, l’échelle et le schéma guidage de schémas de la colonne.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Représente une colonne spécifique prise en charge par le fournisseur. Vous pouvez spécifier la taille de la colonne.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Représente une colonne spécifique prise en charge par le fournisseur. Il suppose que le type de colonne est une chaîne.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Représente une colonne spécifique prise en charge par le fournisseur. Comme PROVIDER_COLUMN_ENTRY_LENGTH, mais vous permet également de spécifier le type de données de la colonne ainsi que la taille.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Représente une colonne spécifique prise en charge par le fournisseur. Il suppose que le type de colonne est une chaîne de caractères Unicode.|

## <a name="schema-rowset-macros"></a>Schema Rowset Macros

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Marque le début d’une carte schéma.|
|[END_SCHEMA_MAP](#end_schema_map)|Marque la fin d’une carte de schéma.|
|[SCHEMA_ENTRY](#schema_entry)|Associe un GUID à une classe.|

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Marque le début d’une propriété située dans une carte de propriété définie.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Paramètres

*Guid*<br/>
[dans] La propriété GUID.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Marque le début d’une propriété située dans une carte de propriété définie.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Paramètres

*Guid*<br/>
[dans] La propriété GUID.

*Drapeaux*<br/>
[dans] UPROPSET_HIDDEN pour les ensembles de propriété que vous ne souhaitez pas exposer, ou UPROPSET_PASSTHROUGH pour un fournisseur exposant des propriétés définies en dehors de la portée du fournisseur.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Marque le début des entrées de carte définies par propriété.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Paramètres

*Classe*<br/>
[dans] La classe dans laquelle cet ensemble de propriété est spécifié. Un ensemble de propriété peut être spécifié dans les objets OLE DB suivants :

- [Objets source de données](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Objets de session](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Commandes](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Exemple

Voici un exemple de carte de propriété :

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

Cette macro-chaîne de groupes immobiliers ensemble.

#### <a name="syntax"></a>Syntaxe

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Paramètres

*Classe Chaîne*<br/>
[dans] Le nom de la classe à la chaîne des propriétés pour. Il s’agit d’une classe générée par l’ASSISTANT de projet ATL qui contient déjà une carte (comme une session, une commande ou une classe d’objets source de données).

#### <a name="remarks"></a>Notes

Vous pouvez enchaîner un ensemble de propriété d’une autre classe à votre propre classe, puis accéder aux propriétés directement à partir de votre classe.

> [!CAUTION]
> Utilisez cette macro avec parcimonie. Une mauvaise utilisation peut faire échouer les tests de conformité OLE DB.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Marque la fin d’un ensemble de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Paramètres

*Guid*<br/>
[dans] La propriété GUID.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

Marque la fin des entrées de carte définies par propriété.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

Représente une propriété spécifique dans un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Paramètres

*dwPropID*<br/>
[in] Valeur [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.

#### <a name="remarks"></a>Notes

Cette macro attribue à la propriété de type `DWORD` une valeur par défaut définie dans ATLDB.H. Pour attribuer à la propriété une valeur de votre choix, utilisez [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Pour définir `VARTYPE` le et [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) pour la propriété en même temps, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Représente une propriété spécifique dans un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Paramètres

*dwPropID*<br/>
[in] Valeur [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.

*vt*<br/>
[in] `VARTYPE` de cette entrée de propriété. (Défini en wtypes.h)

*dwFlags*<br/>
[in] Valeur [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) décrivant cette entrée de propriété.

*value*<br/>
[in] Valeur de propriété de type `DWORD`.

*Options*<br/>
DBPROPOPTIONS_REQUIRED ou DBPROPOPTIONS_SETIFCHEAP. Normalement, un fournisseur n’a pas besoin de définir des *options* puisqu’il est défini par le consommateur.

#### <a name="remarks"></a>Notes

Avec cette macro, vous pouvez spécifier directement la valeur de propriété de type `DWORD` , ainsi que les options et les indicateurs. Pour affecter simplement à une propriété une valeur par défaut définie dans ATLDB.H, utilisez [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pour affecter à une propriété une valeur de votre choix, sans définir aucune option ou indicateur, utilisez [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

Représente une propriété spécifique dans un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Paramètres

*dwPropID*<br/>
[in] Valeur [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.

*value*<br/>
[in] Valeur de propriété de type `DWORD`.

#### <a name="remarks"></a>Notes

Avec cette macro, vous pouvez spécifier directement la valeur de la propriété de type `DWORD`. Définir la propriété à la valeur par défaut définie dans ATLDB. H, utiliser [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pour définir la valeur, les drapeaux et les options pour la propriété, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Marque le début des entrées de carte de colonne fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Paramètres

*la Classe*<br/>
[dans] Le nom de la classe à laquelle cette carte appartient.

#### <a name="example"></a>Exemple

Voici une carte de colonne de fournisseur d’échantillons :

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Marque la fin des entrées de carte de colonne du fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Exemple

Voir [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*Membre*<br/>
[dans] La variable `dataClass` du membre correspondant à la colonne.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*dbtype*<br/>
[dans] Le type de données dans [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Membre*<br/>
[dans] La variable `dataClass` du membre dans ce qui stocke les données.

#### <a name="remarks"></a>Notes

Vous permet de spécifier le type de données de colonne.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*Drapeaux*<br/>
[dans] Précise comment les données sont retournées. Voir `dwFlags` la description dans [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
[dans] La taille de la colonne.

*dbtype*<br/>
[dans] Indique le type de données de la valeur. Voir `wType` la description dans [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Précision*<br/>
[dans] Indique la précision à utiliser lors de l’obtention de données si *dbType* est DBTYPE_NUMERIC ou DBTYPE_DECIMAL. Voir `bPrecision` la description dans [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Échelle*<br/>
[dans] Indique l’échelle à utiliser lors de l’obtention de données si dbType est DBTYPE_NUMERIC ou DBTYPE_DECIMAL. Voir `bScale` la description dans [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Guid*<br/>
Un schéma encastré GUID. Voir [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans la *référence du programmeur OLE DB* pour une liste de rames de schémas et leurs GUIDs.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la taille, le type de données, la précision, l’échelle et le schéma guidage de schémas de la colonne.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*Taille*<br/>
[dans] La taille de la colonne dans les octets.

*Membre*<br/>
[dans] La variable `dataClass` de membre dans ce stocke les données de colonne.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la taille de la colonne.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*Membre*<br/>
[dans] La variable du membre dans la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Utilisez cette macro lorsque les données de la colonne sont supposées être [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*dbtype*<br/>
[dans] Le type de données dans [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Taille*<br/>
[dans] La taille de la colonne dans les octets.

*Membre*<br/>
[dans] La variable du membre dans la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Semblable à [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) mais vous permet également de spécifier le type de données de la colonne ainsi que la taille.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Représente une colonne spécifique prise en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[dans] Le nom de la colonne.

*Ordinal*<br/>
[dans] Le numéro de colonne. Sauf si la colonne est une colonne De signet, le numéro de colonne ne doit pas être 0.

*Membre*<br/>
[dans] La variable du membre dans la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Utilisez cette macro lorsque les données de colonne est une chaîne de caractère Unicode non terminée, [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Dénote le début d’une carte de schéma.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Paramètres

*Classe Schema*<br/>
La classe qui contient le MAP. Typiquement, ce sera la classe de session.

#### <a name="remarks"></a>Notes

Voir [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le Windows SDK pour plus d’informations sur les rames de schémas.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Dénote la fin de la carte du schéma.

#### <a name="syntax"></a>Syntaxe

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Notes

Pour plus d’informations, voir [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Associe un GUID à une classe.

#### <a name="syntax"></a>Syntaxe

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Paramètres

*Guid*<br/>
Un schéma encastré GUID. Voir [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans la *référence du programmeur OLE DB* pour une liste de rames de schémas et leurs GUIDs.

*RowsetClass (en anglais)*<br/>
La classe qui sera créée pour représenter le schéma.

#### <a name="remarks"></a>Notes

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) peut alors interroger la carte pour une liste de GUIDs, ou il peut créer un jeu de ligne si elle est donnée un GUID. Le schéma de `IDBSchemaRowsetImpl` jeu crée est `CRowsetImpl`similaire à une classe `Execute` dérivée de la norme, sauf qu’il doit fournir une méthode qui a la signature suivante:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Cette `Execute` fonction remplit les données du rowset. L’ASSISTANT de projet ATL crée, comme décrit dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans la *référence du programmeur OLE DB*, trois premiers ensembles de schémas dans le projet pour chacun des trois schémas obligatoires OLE DB :

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

L’assistant ajoute également trois entrées correspondantes dans la carte du schéma. Voir [Création d’un fournisseur de gabarit OLE DB](../../data/oledb/creating-an-ole-db-provider.md) pour plus d’informations sur l’utilisation de l’assistant pour créer un fournisseur.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB Provider Templates Référence](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Macros pour OLE DB Provider Templates](../../data/oledb/macros-for-ole-db-provider-templates.md)
