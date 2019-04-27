---
title: Macros pour les modèles du fournisseur OLE DB
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
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
ms.openlocfilehash: f5cf5e8ebadcc48dbd040225496f0a437b92555c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152707"
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros pour les modèles du fournisseur OLE DB

Les macros de fournisseur de modèles OLE DB offrent des fonctionnalités dans les catégories suivantes :

## <a name="property-set-map-macros"></a>Macros de mappage de propriété Set

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Marque le début d’un jeu de propriétés.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Marque le début d’un jeu de propriétés.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Marque le début d’une propriété définie qui peut être masqué ou défini en dehors de la portée du fournisseur.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Chaîne ensemble les groupes de propriétés.|
|[END_PROPERTY_SET](#end_property_set)|Marque la fin d’un jeu de propriétés.|
|[END_PROPSET_MAP](#end_propset_map)|Marque la fin d’un mappage de jeu de propriétés.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Définit une propriété spécifique dans une propriété avec une valeur par défaut.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Définit une propriété spécifique dans une propriété avec une valeur fournie par vous. Vous permet également de définir les options et les indicateurs.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Définit une propriété spécifique dans une propriété avec une valeur fournie par vous.|

## <a name="column-map-macros"></a>Macros de mappage de colonne

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Marque le début des entrées de mappage de colonne de fournisseur.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Marque la fin des entrées de mappage de colonne de fournisseur.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Représente une colonne spécifique est pris en charge par le fournisseur.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Représente une colonne spécifique est pris en charge par le fournisseur. Vous pouvez spécifier le type de données de colonne.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Représente une colonne spécifique est pris en charge par le fournisseur. Vous pouvez spécifier la taille de la colonne, type de données, précision, échelle et GUID du jeu de lignes de schéma.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Représente une colonne spécifique est pris en charge par le fournisseur. Vous pouvez spécifier la taille de colonne.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Représente une colonne spécifique est pris en charge par le fournisseur. Il suppose que le type de colonne est une chaîne.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Représente une colonne spécifique est pris en charge par le fournisseur. Comme PROVIDER_COLUMN_ENTRY_LENGTH, mais vous permet également de spécifier le type de données de la colonne, ainsi que la taille.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Représente une colonne spécifique est pris en charge par le fournisseur. Il suppose que le type de colonne est une chaîne de caractères Unicode.|

## <a name="schema-rowset-macros"></a>Macros d’ensemble de lignes de schéma

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Marque le début d’un mappage de schéma.|
|[END_SCHEMA_MAP](#end_schema_map)|Marque la fin d’un mappage de schéma.|
|[SCHEMA_ENTRY](#schema_entry)|Associe un GUID à une classe.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET

Mappage d’ensemble de marque le début d’une propriété défini dans une propriété.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] La propriété GUID.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

Mappage d’ensemble de marque le début d’une propriété défini dans une propriété.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] La propriété GUID.

*flags*<br/>
[in] UPROPSET_HIDDEN pour les jeux de propriétés que vous ne souhaitez pas exposer ou UPROPSET_PASSTHROUGH pour un fournisseur d’exposer des propriétés définies en dehors de la portée du fournisseur.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

Marque le début de la propriété définie des entrées de mappage.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Paramètres

*Classe*<br/>
[in] La classe dans laquelle cette propriété la valeur est spécifiée. Un jeu de propriétés peut être spécifié dans les objets OLE DB suivants :

- [Objets Source de données](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Objets de session](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Commandes](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Exemple

Voici un exemple de mappage de jeu de propriétés :

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET

Cette macro chaîne ensemble les groupes de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Paramètres

*ChainClass*<br/>
[in] Le nom de la classe à des propriétés de chaîne. Il s’agit d’une classe générée par l’Assistant Projet ATL qui contient déjà un mappage (par exemple, une session, de commande ou de données source classe d’objet).

#### <a name="remarks"></a>Notes

Vous pouvez chaîner un jeu de propriétés à partir d’une autre classe à votre propre classe, puis accéder aux propriétés directement à partir de votre classe.

> [!CAUTION]
>  Utilisez cette macro avec parcimonie. Utilisation incorrecte peut entraîner un consommateur à échouer les tests de compatibilité OLE DB.

### <a name="end_property_set"></a> END_PROPERTY_SET

Marque la fin d’un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] La propriété GUID.

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a> END_PROPSET_MAP

Marque la fin de la propriété définie des entrées de mappage.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

Représente une propriété spécifique dans un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Paramètres

*dwPropID*<br/>
[in] Valeur [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.

#### <a name="remarks"></a>Notes

Cette macro attribue à la propriété de type `DWORD` une valeur par défaut définie dans ATLDB.H. Pour attribuer à la propriété une valeur de votre choix, utilisez [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Pour définir le `VARTYPE` et [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) pour la propriété en même temps, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

Représente une propriété spécifique dans un jeu de propriétés.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Paramètres

*dwPropID*<br/>
[in] Valeur [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.

*vt*<br/>
[in] `VARTYPE` de cette entrée de propriété. (Défini dans wtypes.h)

*dwFlags*<br/>
[in] Valeur [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) décrivant cette entrée de propriété.

*valeur*<br/>
[in] Valeur de propriété de type `DWORD`.

*options*<br/>
DBPROPOPTIONS_REQUIRED ou DBPROPOPTIONS_SETIFCHEAP. En règle générale, un fournisseur sans devoir définir *options* dans la mesure où elle est définie par le consommateur.

#### <a name="remarks"></a>Notes

Avec cette macro, vous pouvez spécifier directement la valeur de propriété de type `DWORD` , ainsi que les options et les indicateurs. Pour affecter simplement à une propriété une valeur par défaut définie dans ATLDB.H, utilisez [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pour affecter à une propriété une valeur de votre choix, sans définir aucune option ou indicateur, utilisez [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

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

Avec cette macro, vous pouvez spécifier directement la valeur de propriété de type `DWORD`. Pour définir la propriété valeur par défaut définie dans ATLDB. H, utilisez [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pour définir la valeur, les indicateurs et les options de la propriété, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Exemple

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

Marque le début des entrées de mappage de colonne de fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Paramètres

*theClass*<br/>
[in] Le nom de la classe à que laquelle appartient ce mappage.

#### <a name="example"></a>Exemple

Voici un exemple de mappage de colonne fournisseur :

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

Marque la fin des entrées de mappage de colonne de fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Exemple

Consultez [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*member*<br/>
[in] La variable de membre dans `dataClass` correspondant à la colonne.

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*dbtype*<br/>
[in] Le type de données dans [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*member*<br/>
[in] La variable de membre dans `dataClass` qui stocke les données.

#### <a name="remarks"></a>Notes

Vous permet de spécifier le type de données de colonne.

#### <a name="example"></a>Exemple

Consultez [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*flags*<br/>
[in] Spécifie la façon dont les données sont retournées. Consultez le `dwFlags` description dans [Structures DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
[in] La taille de la colonne.

*dbtype*<br/>
[in] Indique le type de données de la valeur. Consultez le `wType` description dans [Structures DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*precision*<br/>
[in] Indique la précision à utiliser lors de l’obtention des données si *dbType* soit DBTYPE_NUMERIC DBTYPE_DECIMAL. Consultez le `bPrecision` description dans [Structures DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*scale*<br/>
[in] Indique l’échelle à utiliser lors de l’obtention des données si dbType est DBTYPE_NUMERIC ou DBTYPE_DECIMAL. Consultez le `bScale` description dans [Structures DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*guid*<br/>
Un GUID de lignes du schéma. Consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *de référence du programmeur OLE DB* pour obtenir la liste des ensembles de lignes de schéma et de leurs GUID.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la taille de la colonne, type de données, précision, échelle et GUID du jeu de lignes de schéma.

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*size*<br/>
[in] La taille de la colonne en octets.

*member*<br/>
[in] La variable de membre dans `dataClass` qui stocke les données de colonne.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la taille de la colonne.

#### <a name="example"></a>Exemple

Consultez [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*member*<br/>
[in] La variable de membre de la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Utilisez cette macro, lorsque les données de colonne sont supposées être [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Exemple

Consultez [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*dbtype*<br/>
[in] Le type de données dans [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*size*<br/>
[in] La taille de la colonne en octets.

*member*<br/>
[in] La variable de membre de la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Semblable à [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , mais vous permet également de spécifier le type de données de la colonne, ainsi que la taille.

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

Représente une colonne spécifique est pris en charge par le fournisseur.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
[in] Le nom de colonne.

*ordinal*<br/>
[in] Le numéro de colonne. À moins que la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.

*member*<br/>
[in] La variable de membre de la classe de données qui stocke les données.

#### <a name="remarks"></a>Notes

Utilisez cette macro, lorsque les données de la colonne sont une chaîne de caractères Unicode, de nul [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

Indique le début d’un mappage de schéma.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Paramètres

*SchemaClass*<br/>
La classe qui contient le mappage. En général, il s’agit de la classe session.

#### <a name="remarks"></a>Notes

Consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le SDK Windows pour plus d’informations sur les ensembles de lignes de schéma.

### <a name="end_schema_map"></a> END_SCHEMA_MAP

Indique la fin du mappage de schéma.

#### <a name="syntax"></a>Syntaxe

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IDBSchemaRowsetImpl, classe](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a> SCHEMA_ENTRY

Associe un GUID à une classe.

#### <a name="syntax"></a>Syntaxe

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
Un GUID de lignes du schéma. Consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *de référence du programmeur OLE DB* pour obtenir la liste des ensembles de lignes de schéma et de leurs GUID.

*rowsetClass*<br/>
La classe qui sera créée pour représenter l’ensemble de lignes de schéma.

#### <a name="remarks"></a>Notes

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) pouvez ensuite interroger la carte pour obtenir la liste de GUID, ou il peut créer un ensemble de lignes s’il est doté d’un GUID. L’ensemble de lignes de schéma `IDBSchemaRowsetImpl` crée est similaire à une norme `CRowsetImpl`-classe dérivée, à ceci près qu’il doit fournir un `Execute` méthode qui a la signature suivante :

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Cela `Execute` fonction remplit les données de l’ensemble de lignes. L’Assistant Projet ATL crée, comme décrit dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans le *de référence du programmeur OLE DB*, trois initiale des ensembles de lignes de schéma dans le projet pour chacun des trois schémas OLE DB obligatoires :

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

L’Assistant ajoute également trois entrées correspondantes dans le mappage de schéma. Consultez [création d’un fournisseur OLE DB modèle](../../data/oledb/creating-an-ole-db-provider.md) pour plus d’informations sur l’utilisation de l’Assistant pour créer un fournisseur.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Référence des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)