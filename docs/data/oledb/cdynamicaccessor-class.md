---
title: CDynamicAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 31cc996b8beedadf9cba5a46b3b4da20e19268b0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498680"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (la structure sous-jacente de la base de données).

## <a name="syntax"></a>Syntax

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli. h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddBindEntry](#addbindentry)|Ajoute une entrée de liaison aux colonnes de sortie lors de la substitution de l’accesseur par défaut.|
|[CDynamicAccessor](#cdynamicaccessor)|Instancie et initialise l' `CDynamicAccessor` objet.|
|[Close](#close)|Annule la liaison de toutes les colonnes, libère la mémoire allouée et libère le pointeur d’interface [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) dans la classe.|
|[GetBlobHandling](#getblobhandling)|Récupère la valeur de gestion des objets BLOB pour la ligne actuelle.|
|[GetBlobSizeLimit](#getblobsizelimit)|Récupère la taille maximale d’objet BLOB en octets.|
|[GetBookmark](#getbookmark)|Récupère le signet pour la ligne actuelle.|
|[GetColumnCount](#getcolumncount)|Récupère le nombre de colonnes dans l’ensemble de lignes.|
|[GetColumnFlags](#getcolumnflags)|Récupère les caractéristiques de colonne.|
|[GetColumnInfo](#getcolumninfo)|Récupère les métadonnées de la colonne.|
|[GetColumnName](#getcolumnname)|Récupère le nom d’une colonne spécifiée.|
|[GetColumnType](#getcolumntype)|Récupère le type de données d’une colonne spécifiée.|
|[GetLength](#getlength)|Récupère la longueur maximale possible d’une colonne en octets.|
|[GetOrdinal](#getordinal)|Récupère l’index de colonne en fonction d’un nom de colonne.|
|[GetStatus](#getstatus)|Récupère l’état d’une colonne spécifiée.|
|[GetValue](#getvalue)|Récupère les données de la mémoire tampon.|
|[SetBlobHandling](#setblobhandling)|Définit la valeur de gestion des objets BLOB pour la ligne actuelle.|
|[SetBlobSizeLimit](#setblobsizelimit)|Définit la taille maximale de l’objet BLOB en octets.|
|[SetLength](#setlength)|Définit la longueur de la colonne en octets.|
|[SetStatus](#setstatus)|Définit l’état d’une colonne spécifiée.|
|[SetValue](#setvalue)|Stocke les données dans la mémoire tampon.|

## <a name="remarks"></a>Remarques

Utilisez `CDynamicAccessor` des méthodes pour obtenir des informations sur les colonnes, telles que les noms de colonnes, le nombre de colonnes, le type de données, etc. Vous utilisez ensuite ces informations de colonne pour créer un accesseur de manière dynamique au moment de l’exécution.

Les informations de colonne sont stockées dans une mémoire tampon qui est créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide de [GetValue](#getvalue).

Pour obtenir une discussion et des exemples d’utilisation des classes d’accesseur dynamiques, consultez [utilisation d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a> CDynamicAccessor :: AddBindEntry

Ajoute une entrée de liaison aux colonnes de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Paramètres

*info*<br/>
dans `DBCOLUMNINFO` Structure contenant des informations sur les colonnes. Consultez « structures DBCOLUMNINFO » dans [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Remarques

Utilisez cette méthode lors de la substitution de l’accesseur par défaut créé avec `CDynamicAccessor` (consultez [comment extraire des données ?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a> CDynamicAccessor :: CDynamicAccessor

Instancie et initialise l' `CDynamicAccessor` objet.

### <a name="syntax"></a>Syntaxe

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Paramètres

*eBlobHandling*<br/>
Spécifie la manière dont les données BLOB (Binary Large Object) doivent être gérées. La valeur par défaut est DBBLOBHANDLING_DEFAULT. Pour obtenir une description des valeurs de DBBLOBHANDLINGENUM, consultez [SetBlobHandling](#setblobhandling) .

*nBlobSize*<br/>
Taille maximale d’objet BLOB en octets ; les données de colonne sur cette valeur sont traitées comme un objet BLOB. La valeur par défaut est 8 000. Pour plus d’informations, consultez [SetBlobSizeLimit](#setblobsizelimit) .

### <a name="remarks"></a>Remarques

Si vous utilisez le constructeur pour initialiser l' `CDynamicAccessor` objet, vous pouvez spécifier comment il doit lier des objets BLOB. Les objets BLOB peuvent contenir des données binaires telles que des graphiques, du son ou du code compilé. Le comportement par défaut consiste à traiter les colonnes de plus de 8 000 octets comme des objets BLOB et à essayer de les lier à un `ISequentialStream` objet. Toutefois, vous pouvez spécifier une valeur différente pour la taille de l’objet BLOB.

Vous pouvez également spécifier la manière dont `CDynamicAccessor` gère les données de colonne qui sont qualifiées de données BLOB : elles peuvent gérer les données d’objets BLOB de la manière par défaut ; elles peuvent ignorer (ne lie pas) les données BLOB ou lier des données BLOB dans la mémoire allouée par le fournisseur.

## <a name="cdynamicaccessorclose"></a><a name="close"></a> CDynamicAccessor :: Close

Annule la liaison de toutes les colonnes, libère la mémoire allouée et libère le pointeur d’interface [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) dans la classe.

### <a name="syntax"></a>Syntax

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a> CDynamicAccessor :: GetBlobHandling

Récupère la valeur de gestion des objets BLOB pour la ligne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Notes

Retourne la valeur de gestion des objets BLOB *eBlobHandling* définie par [SetBlobHandling](#setblobhandling).

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a> CDynamicAccessor :: GetBlobSizeLimit

Récupère la taille maximale d’objet BLOB en octets.

### <a name="syntax"></a>Syntaxe

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Notes

Retourne la valeur de gestion des objets BLOB *nBlobSize* définie par [SetBlobSizeLimit](#setblobsizelimit).

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a> CDynamicAccessor :: GetBookmark

Récupère le signet pour la ligne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Paramètres

*pBookmark*<br/>
à Pointeur vers l’objet [CBookmark](../../data/oledb/cbookmark-class.md) .

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Remarques

Vous devez définir `DBPROP_IRowsetLocate` sur VARIANT_TRUE pour récupérer un signet.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a> CDynamicAccessor :: GetColumnCount

Récupère le nombre de colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Nombre de colonnes récupérées.

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a> CDynamicAccessor :: GetColumnFlags

Récupère les caractéristiques de colonne.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pFlags*<br/>
à Pointeur vers un masque de masque qui décrit les caractéristiques de colonne. Consultez « type énuméré DBCOLUMNFLAGS » dans [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si les caractéristiques des colonnes sont récupérées avec succès. Sinon, elle retourne **`false`** .

### <a name="remarks"></a>Remarques

Le numéro de colonne est décalé par rapport à un. La colonne zéro est un cas particulier ; Il s’agit du signet, s’il est disponible.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a> CDynamicAccessor :: GetColumnInfo

Retourne les métadonnées de colonne exigées par la plupart des consommateurs.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Paramètres

*pRowset*<br/>
dans Pointeur vers l’interface [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) .

*pColumns*<br/>
à Pointeur vers la mémoire dans lequel retourner le nombre de colonnes dans l’ensemble de lignes ; ce nombre inclut la colonne de signets, le cas échéant.

*ppColumnInfo*<br/>
à Pointeur vers la mémoire dans lequel retourner un tableau de `DBCOLUMNINFO` structures. Consultez « structures DBCOLUMNINFO » dans [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

*ppStringsBuffer*<br/>
à Pointeur vers la mémoire dans lequel retourner un pointeur vers le stockage pour toutes les valeurs de chaîne (noms utilisés dans *ColumnID* ou pour *pwszName*) dans un bloc d’allocation unique.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Remarques

Pour plus d’informations sur les types de données, et, consultez [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *OLE DB Guide de référence du programmeur* `DBORDINAL` `DBCOLUMNINFO` `OLECHAR` .

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a> CDynamicAccessor :: GetColumnName

Récupère le nom de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

### <a name="return-value"></a>Valeur renvoyée

Nom de la colonne spécifiée.

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a> CDynamicAccessor :: GetColumnType

Récupère le type de données d’une colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pType*<br/>
à Pointeur vers le type de données de la colonne spécifiée.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a> CDynamicAccessor :: GetLength

Récupère la longueur de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

*pLength*<br/>
à Pointeur vers l’entier contenant la longueur de la colonne en octets.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si la colonne spécifiée est trouvée. Sinon, cette fonction retourne **`false`** .

### <a name="remarks"></a>Remarques

La première substitution prend le numéro de colonne, tandis que les deuxième et troisième remplacements prennent respectivement le nom de colonne au format ANSI ou Unicode.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a> CDynamicAccessor :: GetOrdinal

Récupère le numéro de colonne en fonction d’un nom de colonne.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Paramètres

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

*pOrdinal*<br/>
à Pointeur vers le numéro de colonne.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** une valeur si une colonne portant le nom spécifié est trouvée. Sinon, cette fonction retourne **`false`** .

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a> CDynamicAccessor :: GetStatus

Récupère l’état de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

*pStatus*<br/>
à Pointeur vers la variable qui contient l’état de la colonne. Pour plus d’informations, consultez [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si la colonne spécifiée est trouvée. Sinon, cette fonction retourne **`false`** .

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a> CDynamicAccessor :: GetValue

Récupère les données pour une colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>Paramètres

*ctype*<br/>
dans Paramètre basé sur un modèle qui gère tout type de données, à l’exception des types de chaînes ( `CHAR*` , `WCHAR*` ), qui nécessitent un traitement spécial. `GetValue` utilise le type de données approprié en fonction de ce que vous spécifiez ici.

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pColumnName*<br/>
dans Nom de la colonne.

*pData*<br/>
à Pointeur vers le contenu de la colonne spécifiée.

### <a name="return-value"></a>Valeur renvoyée

Si vous souhaitez passer des données de type chaîne, utilisez les versions non basées sur des modèles de `GetValue` . Les versions non basées sur des modèles de cette méthode retournent **`void*`** , qui pointe vers la partie de la mémoire tampon qui contient les données de colonne spécifiées. Retourne la valeur NULL si la colonne est introuvable.

Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue` . Les versions basées sur un modèle retournent **`true`** en cas de réussite ou **`false`** d’échec.

### <a name="remarks"></a>Remarques

Utilisez les versions sans modèle pour retourner les colonnes qui contiennent des chaînes et les versions basées sur des modèles pour les colonnes qui contiennent d’autres types de données.

En mode débogage, vous obtiendrez une assertion si la taille de *pData* est différente de la taille de la colonne à laquelle il pointe.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a> CDynamicAccessor :: SetBlobHandling

Définit la valeur de gestion des objets BLOB pour la ligne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Paramètres

*eBlobHandling*<br/>
Spécifie comment les données d’objet BLOB doivent être gérées. Il peut avoir les valeurs suivantes :

- DBBLOBHANDLING_DEFAULT : gérez les données de colonne supérieures à *nBlobSize* (comme défini par `SetBlobSizeLimit` ) en tant que données BLOB et récupérez-les par le biais d’un `ISequentialStream` `IStream` objet ou. Cette option tente de lier chaque colonne contenant des données supérieures à *nBlobSize* ou listées comme données BLOB DBTYPE_IUNKNOWN.

- DBBLOBHANDLING_NOSTREAMS : gérez les données de colonne supérieures à *nBlobSize* (comme défini par `SetBlobSizeLimit` ) en tant que données d’objet BLOB et récupérez-les par référence dans la mémoire allouée par le fournisseur et la mémoire appartenant au consommateur. Cette option est utile pour les tables qui contiennent plusieurs colonnes BLOB, et le fournisseur ne prend en charge qu’un seul `ISequentialStream` objet par accesseur.

- DBBLOBHANDLING_SKIP : ignorer (ne pas lier) les colonnes qui sont qualifiées d’objets BLOB contenants (l’accesseur ne lie ni ne récupère la valeur de colonne, mais il récupère toujours l’État et la longueur de la colonne).

### <a name="remarks"></a>Remarques

Vous devez appeler `SetBlobHandling` avant d'appeler `Open`.

La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit la valeur de la gestion des objets BLOB sur DBBLOBHANDLING_DEFAULT.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a> CDynamicAccessor :: SetBlobSizeLimit

Définit la taille maximale de l’objet BLOB en octets.

### <a name="syntax"></a>Syntaxe

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Paramètres

*nBlobSize*<br/>
Spécifie la taille limite de l’objet BLOB.

### <a name="remarks"></a>Remarques

Définit la taille maximale des objets BLOB en octets ; les données de colonne supérieures à cette valeur sont traitées comme un objet BLOB. Certains fournisseurs offrent des tailles extrêmement élevées pour les colonnes (par exemple, 2 Go). Plutôt que de tenter d’allouer de la mémoire pour une colonne de cette taille, vous essayez généralement de lier ces colonnes en tant qu’objets BLOB. De cette façon, vous n’êtes pas obligé d’allouer toute la mémoire, mais vous pouvez toujours lire toutes les données sans crainte de tronquer. Toutefois, dans certains cas, vous souhaiterez peut-être forcer `CDynamicAccessor` à lier des colonnes de grande taille dans leurs types de données natifs. Pour ce faire, appelez `SetBlobSizeLimit` avant d’appeler `Open` .

La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit la taille maximale d’objet BLOB sur une valeur par défaut de 8 000 octets.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a> CDynamicAccessor :: SetLength

Définit la longueur de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*nLength*<br/>
dans Longueur de la colonne en octets.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si la longueur de colonne spécifiée est correctement définie. Sinon, cette fonction retourne **`false`** .

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a> CDynamicAccessor :: SetStatus

Définit l’état de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*statut*<br/>
dans État de la colonne. Pour plus d’informations, consultez [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si l’état de colonne spécifié est correctement défini. Sinon, cette fonction retourne **`false`** .

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a> CDynamicAccessor :: SetValue

Stocke les données dans une colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>Paramètres

*ctype*<br/>
dans Paramètre basé sur un modèle qui gère tout type de données, à l’exception des types de chaînes ( `CHAR*` , `WCHAR*` ), qui nécessitent un traitement spécial. `GetValue` utilise le type de données approprié en fonction de ce que vous spécifiez ici.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères contenant le nom de la colonne.

*data*<br/>
dans Pointeur vers la mémoire qui contient les données.

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

### <a name="return-value"></a>Valeur renvoyée

Si vous souhaitez définir des données de type chaîne, utilisez les versions non basées sur des modèles de `GetValue` . Les versions non basées sur des modèles de cette méthode retournent **`void*`** , qui pointe vers la partie de la mémoire tampon qui contient les données de colonne spécifiées. Retourne la valeur NULL si la colonne est introuvable.

Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue` . Les versions basées sur un modèle retournent **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)
