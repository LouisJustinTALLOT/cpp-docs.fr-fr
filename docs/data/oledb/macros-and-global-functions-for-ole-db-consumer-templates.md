---
title: Macros et fonctions globales pour les modèles du consommateur OLE DB
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369823"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros et fonctions globales pour les modèles du consommateur OLE DB

Les modèles de consommation OLE DB comprennent les macros et les fonctions mondiales suivantes :

## <a name="global-functions"></a>Fonctions globales

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Décharge les informations d’enregistrement d’erreur OLE DB à l’appareil de décharge si une erreur est retournée.|

## <a name="accessor-map-macros"></a>Macros carte d’accesseur

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Marque le début d’une entrée d’accesseur.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Marque le début des entrées de mappage d’accesseur.|
|[END_ACCESSOR](#end_accessor)|Marque la fin d’une entrée d’accesseur.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Marque la fin des entrées de carte de l’accesseur.|

## <a name="column-map-macros"></a>Macros de carte de colonne

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Marque le début des entrées de la carte de colonne dans la classe d’enregistrement de l’utilisateur.|
|[BLOB_ENTRY](#blob_entry)|Utilisé pour lier un grand objet binaire (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Signale la longueur de la colonne de données BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Signale la longueur et l’état de la colonne de données BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Signale l’état de la colonne de données BLOB.|
|[BLOB_NAME](#blob_name)|Utilisé pour lier un grand objet binaire par nom de colonne.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Signale la longueur de la colonne de données BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Signale la longueur et l’état de la colonne de données BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Signale l’état de la colonne de données BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Représente une entrée de signet sur le rame. Une entrée de signet est un type spécial d’entrée de colonne.|
|[COLUMN_ENTRY](#column_entry)|Représente une liaison à une colonne spécifique dans la base de données.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Représente une liaison à la colonne spécifique de la base de données. Supports *type,* *longueur,* *précision,* *échelle,* et paramètres *d’état.*|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge la variable *de longueur.*|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge les paramètres *d’état* et *de longueur.*|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge la *précision* et les paramètres *d’échelle.*|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge la variable de *longueur,* *la précision* et les paramètres *d’échelle.*|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge les variables *de l’état* et *de la longueur,* *la précision* et les paramètres *d’échelle.*|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge la variable de *statut,* *la précision* et les paramètres *d’échelle.*|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge la variable *de statut.*|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Représente une liaison à une colonne spécifique dans la base de données. Prend en charge le paramètre *de type.*|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Représente une liaison à la colonne spécifique de la base de données. Prend en charge les paramètres *de type* et *de taille.*|
|[COLUMN_NAME](#column_name)|Représente une liaison à une colonne spécifique dans la base de données par nom.|
|[COLUMN_NAME_EX](#column_name_ex)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications du type de données, de la taille, de la précision, de l’échelle, de la longueur de la colonne et de l’état de la colonne.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de la longueur de la colonne.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de la longueur et du statut de la colonne.|
|[COLUMN_NAME_PS](#column_name_ps)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de précision et d’échelle.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de précision, d’échelle et de longueur de colonne.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de précision, d’échelle, de longueur de colonne et d’état de colonne.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de précision, d’échelle et d’état de colonne.|
|[COLUMN_NAME_STATUS](#column_name_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications de l’état de la colonne.|
|[COLUMN_NAME_TYPE](#column_name_type)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications du type de données.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications du type de données, de la précision et de l’échelle.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications du type et de la taille des données.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge les spécifications du type de données et de l’état de la colonne.|
|[END_COLUMN_MAP](#end_column_map)|Marque la fin des entrées de la carte de colonne.|

## <a name="command-macros"></a>Macros de commandement

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Spécifie la commande qui sera utilisée pour créer le jeu de ligne lors de l’utilisation de la classe [CCommand.](../../data/oledb/ccommand-class.md) Accepte uniquement les types de chaînes correspondant au type d’application spécifié (ANSI ou Unicode). Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Spécifie la commande qui sera utilisée pour créer le jeu de ligne lors de l’utilisation de la classe [CCommand.](../../data/oledb/ccommand-class.md) Prend en charge les applications ANSI et Unicode.|

## <a name="parameter-map-macros"></a>Macros de carte de paramètres

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Marque le début des entrées de carte de paramètres dans la classe d’enregistrement de l’utilisateur.|
|[END_PARAM_MAP](#end_param_map)|Marque la fin des entrées de carte de paramètres.|
|[SET_PARAM_TYPE](#set_param_type)|Spécifie COLUMN_ENTRY macros qui suivent le macro SET_PARAM_TYPE comme entrée, sortie, ou entrée /sortie.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Décharge les informations d’enregistrement d’erreur OLE DB à l’appareil de décharge si une erreur est retournée.

#### <a name="syntax"></a>Syntaxe

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Paramètres

*Herr*<br/>
[dans] Un HRESULT retourné par une fonction membre OLE DB Consumer Template.

#### <a name="remarks"></a>Notes

Si *hErr* n’est `AtlTraceErrorRecords` pas S_OK, décharge les informations d’enregistrement d’erreur OLE DB à l’appareil de décharge (l’onglet **Debug** de la fenêtre de sortie ou un fichier). Les informations sur l’enregistrement d’erreur, qui sont obtenues auprès du fournisseur, comprennent le numéro de rangée, la source, la description, le fichier d’aide, le contexte et le GUID pour chaque saisie d’enregistrement d’erreur. `AtlTraceErrorRecords`décharge cette information uniquement dans les constructions de débogé. Dans les versions, c’est un talon vide qui est optimisé. Pour plus d’informations, voir [CDBErrorInfo Class](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Marque le début d’une entrée d’accesseur.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Paramètres

*num*<br/>
[dans] Le numéro zéro-offset pour l’accesseur dans cette carte d’accesseur.

*bAuto*<br/>
[dans] Précise si cet accesseur est un accesseur automatique ou un accesseur manuel. Si **c’est vrai,** l’accesseur est auto; si **faux,** l’accesseur est manuel. Un accesseur automatique signifie que les données sont récupérées pour vous sur les opérations de déménagement.

#### <a name="remarks"></a>Notes

Dans le cas de plusieurs accesseurs sur un jeu de ligne, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR est complétée par la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP est complétée par la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Exemple

Voir [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Marque le début des entrées de mappage d’accesseur.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
[in] Nom de la classe d’enregistrement utilisateur.

*num*<br/>
[in] Nombre d’accesseurs contenus dans ce mappage d’accesseur.

#### <a name="remarks"></a>Notes

Dans le cas de plusieurs accesseurs sur un jeu de ligne, vous devez spécifier BEGIN_ACCESSOR_MAP au début et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR est complétée par la macro END_ACCESSOR. La carte de l’accesseur est complétée par la macro END_ACCESSOR_MAP.

Si l’enregistrement utilisateur ne comprend qu’un seul accesseur, utilisez la macro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

#### <a name="example"></a>Exemple

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

Marque la fin d’une entrée d’accesseur.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Notes

Pour plusieurs accesseurs sur un jeu de ligne, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR est complétée par la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP est complétée par la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Exemple

Voir [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Marque la fin des entrées de carte de l’accesseur.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Notes

Pour plusieurs accesseurs sur un jeu de ligne, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR est complétée par la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP est complétée par la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Exemple

Voir [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Marque le début d’une entrée de mappage de colonnes.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
[in] Nom de la classe d’enregistrement utilisateur dérivée de `CAccessor`.

#### <a name="remarks"></a>Notes

Cette macro est utilisée dans le cas d’un seul accesseur sur un ensemble de lignes. Si vous avez plusieurs accesseurs sur un ensemble de lignes, utilisez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

La macro BEGIN_COLUMN_MAP est complétée par la macro END_COLUMN_MAP. Cette macro est utilisée quand un seul accesseur est obligatoire dans l’enregistrement utilisateur.

Les colonnes correspondent aux champs de l’ensemble de lignes à lier.

#### <a name="example"></a>Exemple

Voici un exemple de mappage de colonnes et de paramètres :

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="example"></a>Exemple

Voir [comment puis-je récupérer un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également la longueur dans les octets de la colonne BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[out] La longueur (réelle) dans les octets de la colonne BLOB.

#### <a name="example"></a>Exemple

Voir [comment puis-je récupérer un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également la longueur et le statut de la colonne BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[out] La longueur (réelle) dans les octets de la colonne BLOB.

*statut*<br/>
[out] L’état de la colonne de données BLOB.

#### <a name="example"></a>Exemple

Voir [comment puis-je récupérer un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Utilisé avec BEGIN_COLUMN_MAP ou BEGIN_ACCESSOR_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également le statut de la colonne BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[out] L’état du champ BLOB.

#### <a name="example"></a>Exemple

Voir [comment puis-je récupérer un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro prend un nom de colonne au lieu d’un numéro de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="example"></a>Exemple

Voir [comment puis-je récupérer un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_NAME](../../data/oledb/blob-name.md), sauf que cette macro obtient également la longueur dans les octets de la colonne de données BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[out] La longueur (réelle) dans les octets de la colonne BLOB.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_NAME](../../data/oledb/blob-name.md), sauf que cette macro obtient également la longueur et l’état de la colonne de données BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[out] La longueur (réelle) dans les octets de la colonne BLOB.

*statut*<br/>
[out] L’état du champ BLOB.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Utilisé avec BEGIN_COLUMN_MAP et END_COLUMN_MAP pour lier un gros objet binaire ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Semblable à [BLOB_NAME](../../data/oledb/blob-name.md), sauf que cette macro obtient également le statut de la colonne de données BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*IID*<br/>
[dans] Interface GUID, `IDD_ISequentialStream`comme , utilisé pour récupérer le BLOB.

*Drapeaux*<br/>
[dans] Drapeaux en mode stockage tels que définis par `STGM_READ`le modèle de stockage structuré OLE (par exemple, ).

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[out] L’état du champ BLOB.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Lie la colonne de signets.

#### <a name="syntax"></a>Syntaxe

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Paramètres

*variable*<br/>
[dans] La variable à lié à la colonne de signets.

#### <a name="example"></a>Exemple

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

Pour plus d’informations, voir [à l’aide de signets](using-bookmarks.md) et [de classe CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

Représente une liaison sur le ligne à la colonne spécifique dans le ramage.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

La macro COLUMN_ENTRY est utilisée dans les endroits suivants :

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

#### <a name="example"></a>Exemple

Voir les exemples dans les sujets macro, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*wType*<br/>
[dans] Le type de données.

*nLength (en)*<br/>
[dans] La taille des données dans les octets.

*nPrecision*<br/>
[dans] La précision maximale à utiliser lors de `DBTYPE_NUMERIC`l’obtention de données et *wType* est . Sinon, ce paramètre est ignoré.

*nScale (en)*<br/>
[dans] L’échelle à utiliser lors de l’obtention de données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

La macro COLUMN_ENTRY_EX est utilisée dans les endroits suivants :

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

#### <a name="example"></a>Exemple

Voir [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne, en commençant par un. Le signet correspond à la colonne zéro.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

#### <a name="remarks"></a>Notes

Cette macro soutient la variable *de longueur.* Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Utilisez cette macro lorsque vous souhaitez prendre en charge les variables de longueur et d’état. Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne, en commençant par un. Le signet correspond à la colonne zéro.

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Cette macro soutient la variable *de longueur.* Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Utilisez cette macro lorsque vous souhaitez prendre en charge les variables de longueur et d’état. Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Cette macro soutient la variable *de statut.* Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Représente une liaison sur le ligne à la colonne spécifique de la base de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Paramètres

Voir [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB*.

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Cette macro soutient la variable *de statut.* Il est utilisé dans les endroits suivants:

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Représente une liaison à la colonne spécifique de la base de données. Prend en charge le paramètre *de type.*

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*wType*<br/>
[dans] Type de données d’entrée de colonne.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Cette macro est une variante spécialisée de la macro [COLUMN_ENTRY](../../data/oledb/column-entry.md) qui fournit un moyen de spécifier le type de données.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Représente une liaison à la colonne spécifique de la base de données. Prend en charge les paramètres *de type* et *de taille.*

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Paramètres

*nOrdinal*<br/>
[dans] Le numéro de colonne.

*wType*<br/>
[dans] Type de données d’entrée de colonne.

*nLength (en)*<br/>
[dans] Taille de l’entrée de colonne dans les octets.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Cette macro est une variante spécialisée de la macro [COLUMN_ENTRY](../../data/oledb/column-entry.md) qui fournit un moyen de spécifier la taille et le type de données.

### <a name="column_name"></a><a name="column_name"></a>COLUMN_NAME

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_ENTRY](../../data/oledb/column-entry.md), sauf que cette macro prend le nom de colonne au lieu du numéro de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Les macros COLUMN_NAME_ sont utilisées aux mêmes endroits que [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Entre les [macros BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre les [macros BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre les [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données, la taille, la précision, l’échelle, la longueur de colonne, et l’état de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*wType*<br/>
[dans] Le type de données.

*nLength (en)*<br/>
[dans] La taille des données dans les octets.

*nPrecision*<br/>
[dans] La précision maximale à utiliser lors de `DBTYPE_NUMERIC`l’obtention de données et *wType* est . Sinon, ce paramètre est ignoré.

*nScale (en)*<br/>
[dans] L’échelle à utiliser lors de l’obtention de données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la longueur de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la longueur de la colonne et le statut de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la précision et l’échelle.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la précision, l’échelle et la longueur de la colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la précision, l’échelle, la longueur de colonne, et l’état de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*length*<br/>
[dans] La variable à lié à la longueur de la colonne.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la précision, l’échelle et le statut de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*nPrecision*<br/>
[dans] La précision maximale de la colonne que vous souhaitez lier.

*nScale (en)*<br/>
[dans] L’échelle de la colonne que vous souhaitez lier.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le statut de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*wType*<br/>
[dans] Le type de données.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données, la précision et l’échelle.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*wType*<br/>
[dans] Le type de données.

*nPrecision*<br/>
[dans] La précision maximale à utiliser lors de `DBTYPE_NUMERIC`l’obtention de données et *wType* est . Sinon, ce paramètre est ignoré.

*nScale (en)*<br/>
[dans] L’échelle à utiliser lors de l’obtention de données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données et la taille.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*wType*<br/>
[dans] Le type de données.

*nLength (en)*<br/>
[dans] La taille des données dans les octets.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Représente une liaison sur le ligne à la colonne spécifique dans le ramage. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données et le statut de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Paramètres

*pszName (en)*<br/>
[dans] Un pointeur sur le nom de la colonne. Le nom doit être une chaîne Unicode. Vous pouvez y parvenir en mettant un «L» en `L"MyColumn"`face du nom, par exemple: .

*wType*<br/>
[dans] Le type de données.

*statut*<br/>
[dans] La variable à lié à l’état de la colonne.

*data*<br/>
[dans] Le membre de données correspondant dans l’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour obtenir des informations sur l’endroit où les macros COLUMN_NAME_ sont utilisées.

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Marque la fin des entrées de la carte de colonne.

#### <a name="syntax"></a>Syntaxe

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Notes

Il est utilisé avec un seul accesseur sur un ligne. La macro BEGIN_COLUMN_MAP est complétée par la macro END_COLUMN_MAP.

#### <a name="example"></a>Exemple

Voir [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Spécifie la commande qui sera utilisée pour créer le jeu de ligne lors de l’utilisation de la classe [CCommand.](../../data/oledb/ccommand-class.md) Accepte uniquement les types de chaînes correspondant au type d’application spécifié (ANSI ou Unicode).

> [!NOTE]
> Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de la classe d’enregistrement utilisateur (commande).

*szCommand (en)*<br/>
[dans] La chaîne de commande qui sera utilisée pour créer le ligne lors de l’utilisation [de CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Notes

La chaîne de commande que vous spécifiez sera utilisée comme par défaut si vous ne spécifiez pas le texte de commande dans le [CCommand::Méthode ouverte.](../../data/oledb/ccommand-open.md)

Cette macro accepte les chaînes ANSI si vous construisez votre application sous forme de chaînes ANSI, ou Unicode si vous construisez votre application sous le nom d’Unicode. Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND, car le premier accepte les chaînes Unicode, quel que soit le type d’application ANSI ou Unicode.

#### <a name="example"></a>Exemple

Voir [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Spécifie la commande qui sera utilisée pour créer le jeu de ligne lors de l’utilisation de la classe [CCommand.](../../data/oledb/ccommand-class.md) Prend en charge les applications Unicode et ANSI.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de la classe d’enregistrement utilisateur (commande).

*wszCommand wszCommand*<br/>
[dans] La chaîne de commande qui sera utilisée pour créer le ligne lors de l’utilisation [de CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Notes

La chaîne de commande que vous spécifiez sera utilisée comme par défaut si vous ne spécifiez pas le texte de commande dans le [CCommand::Méthode ouverte.](../../data/oledb/ccommand-open.md)

Cette macro accepte les chaînes Unicode, quel que soit le type d’application. Cette macro est préférée à [DEFINE_COMMAND](../../data/oledb/define-command.md) car elle prend en charge unicode ainsi que les applications ANSI.

#### <a name="example"></a>Exemple

Voir [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Marque le début des entrées de carte de paramètres.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
[in] Nom de la classe d’enregistrement utilisateur.

#### <a name="remarks"></a>Notes

Les paramètres sont utilisés par [les commandes](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Exemple

Voir l’exemple pour le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) macro.

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Marque la fin des entrées de carte de paramètres.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Exemple

Voir l’exemple pour le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) macro.

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Spécifie COLUMN_ENTRY macros qui suivent l’entrée macro SET_PARAM_TYPE, la sortie ou l’entrée/sortie.

#### <a name="syntax"></a>Syntaxe

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Paramètres

*type*<br/>
[in] Type à définir pour le paramètre.

#### <a name="remarks"></a>Notes

Les fournisseurs prennent en charge uniquement les types d’entrée/sortie de paramètres qui sont pris en charge par la source de données sous-jacente. Le type est une combinaison `DBPARAMIO` d’une ou plusieurs valeurs (voir [Structures DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans la *référence du programmeur OLE DB )*:

- `DBPARAMIO_NOTPARAM`L’accesseur n’a pas de paramètres. En règle `eParamIO` générale, vous définissez à cette valeur dans les accesseurs de ligne pour rappeler à l’utilisateur que les paramètres sont ignorés.

- `DBPARAMIO_INPUT`Un paramètre d’entrée.

- `DBPARAMIO_OUTPUT`Un paramètre de sortie.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`Le paramètre est à la fois une entrée et un paramètre de sortie.

#### <a name="example"></a>Exemple

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Macros et fonctions mondiales pour OLE DB Consumer Templates](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB Consumer Templates Référence](../../data/oledb/ole-db-consumer-templates-reference.md)
