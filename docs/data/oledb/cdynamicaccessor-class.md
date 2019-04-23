---
title: CDynamicAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
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
- GetColumnFlags
- GetColumnInfo
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
ms.openlocfilehash: 19b8d0c86044e04cc60fd7aab89ec828c46f5fb9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040966"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente de la base de données).

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddBindEntry](#addbindentry)|Ajoute une entrée de liaison pour les colonnes de sortie lors de la substitution de l’accesseur par défaut.|
|[CDynamicAccessor](#cdynamicaccessor)|Instancie et initialise le `CDynamicAccessor` objet.|
|[Fermer](#close)|Annule la liaison de toutes les colonnes, libère la mémoire allouée et libère le [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) pointeur d’interface dans la classe.|
|[GetBlobHandling](#getblobhandling)|Récupère l’objet BLOB de valeur pour la ligne actuelle de gestion.|
|[GetBlobSizeLimit](#getblobsizelimit)|Récupère la taille d’objet BLOB maximale en octets.|
|[GetBookmark](#getbookmark)|Récupère le signet pour la ligne actuelle.|
|[GetColumnCount](#getcolumncount)|Récupère le nombre de colonnes dans l’ensemble de lignes.|
|[GetColumnFlags](#getcolumnflags)|Récupère les caractéristiques de la colonne.|
|[GetColumnInfo](#getcolumninfo)|Récupère les métadonnées de colonne.|
|[GetColumnName](#getcolumnname)|Récupère le nom d’une colonne spécifiée.|
|[GetColumnType](#getcolumntype)|Récupère le type de données d’une colonne spécifiée.|
|[GetLength](#getlength)|Récupère la longueur maximale autorisée d’une colonne en octets.|
|[GetOrdinal](#getordinal)|Récupère l’index de colonne donné un nom de colonne.|
|[GetStatus](#getstatus)|Récupère l’état d’une colonne spécifiée.|
|[GetValue](#getvalue)|Récupère les données à partir de la mémoire tampon.|
|[SetBlobHandling](#setblobhandling)|Définit l’objet BLOB de valeur pour la ligne actuelle de gestion.|
|[SetBlobSizeLimit](#setblobsizelimit)|Définit la taille maximale de BLOB en octets.|
|[SetLength](#setlength)|Définit la longueur de la colonne en octets.|
|[SetStatus](#setstatus)|Définit l’état d’une colonne spécifiée.|
|[SetValue](#setvalue)|Stocke les données dans la mémoire tampon.|

## <a name="remarks"></a>Notes

Utilisez `CDynamicAccessor` méthodes pour obtenir des informations de colonne telles que les noms de colonnes, le nombre de colonnes, type de données et ainsi de suite. Ces informations de colonne permet ensuite de créer un accesseur dynamiquement au moment de l’exécution.

Les informations de colonne sont stockées dans une mémoire tampon qui est créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Pour une discussion et des exemples d’utilisation des classes d’accesseurs dynamiques, consultez [à l’aide d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).

## <a name="addbindentry"></a> CDynamicAccessor::AddBindEntry

Ajoute une entrée de liaison pour les colonnes de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Paramètres

*info*<br/>
[in] Un `DBCOLUMNINFO` structure contenant des informations de colonne. Consultez la section « Structures DBCOLUMNINFO » dans [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Utilisez cette méthode lors de la substitution de l’accesseur par défaut créé avec `CDynamicAccessor` (consultez [comment extraire des données ?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessor"></a> CDynamicAccessor::CDynamicAccessor

Instancie et initialise le `CDynamicAccessor` objet.

### <a name="syntax"></a>Syntaxe

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Paramètres

*eBlobHandling*<br/>
Spécifie la manière dont les données d’objet binaire volumineux (BLOB) doit être gérée. La valeur par défaut est DBBLOBHANDLING_DEFAULT. Consultez [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) pour obtenir une description des valeurs DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
La taille maximale de BLOB en octets ; données de la colonne par rapport à cette valeur sont traitées comme un objet BLOB. La valeur par défaut est 8 000. Consultez [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) pour plus d’informations.

### <a name="remarks"></a>Notes

Si vous utilisez le constructeur pour initialiser le `CDynamicAccessor` de l’objet, vous pouvez spécifier comment il lie les objets BLOB. Objets BLOB peut contenir des données binaires telles que des graphiques, audio ou des codes compilés. Le comportement par défaut consiste à traiter les colonnes dépasse 8 000 octets en tant qu’objets BLOB et essayez de les lier à un `ISequentialStream` objet. Toutefois, vous pouvez spécifier une valeur différente pour la taille de l’objet BLOB.

Vous pouvez également spécifier comment `CDynamicAccessor` gère les données de colonne sont appelées données d’objets BLOB : il peut gérer les données d’objets BLOB de la manière par défaut ; il peut ignorer (ne pas lier) les données BLOB ; ou il peut lier des données BLOB dans la mémoire allouée par le fournisseur.

## <a name="close"></a> CDynamicAccessor::Close

Annule la liaison de toutes les colonnes, libère la mémoire allouée et libère le [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) pointeur d’interface dans la classe.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="getblobhandling"></a> CDynamicAccessor::GetBlobHandling

Récupère l’objet BLOB de valeur pour la ligne actuelle de gestion.

### <a name="syntax"></a>Syntaxe

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Notes

Retourne l’objet BLOB de valeur de la gestion des *eBlobHandling* tels que définis par [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="getblobsizelimit"></a> CDynamicAccessor::GetBlobSizeLimit

Récupère la taille d’objet BLOB maximale en octets.

### <a name="syntax"></a>Syntaxe

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Notes

Retourne l’objet BLOB de valeur de la gestion des *nBlobSize* tels que définis par [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="getbookmark"></a> CDynamicAccessor::GetBookmark

Récupère le signet pour la ligne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Paramètres

*pBookmark*<br/>
[out] Un pointeur vers le [CBookmark](../../data/oledb/cbookmark-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Vous devez définir `DBPROP_IRowsetLocate` à VARIANT_TRUE pour récupérer un signet.

## <a name="getcolumncount"></a> CDynamicAccessor::GetColumnCount

Récupère le nombre de colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de colonnes extraites.

## <a name="getcolumnflags"></a> CDynamicAccessor::GetColumnFlags

Récupère les caractéristiques de la colonne.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*pFlags*<br/>
[out] Pointeur vers un masque de bits qui décrit les caractéristiques de la colonne. Consultez « Type d’énuméré DBCOLUMNFLAGS » dans [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si les caractéristiques de la colonne sont récupérées avec succès. Sinon, elle retourne **False**.

### <a name="remarks"></a>Notes

Le numéro de colonne est décalé à partir d’un. Colonne zéro est un cas particulier. Il est le signet s’il est disponible.

## <a name="getcolumninfo"></a> CDynamicAccessor::GetColumnInfo

Retourne les métadonnées de colonne requises par la plupart des consommateurs.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Paramètres

*pRowset*<br/>
[in] Un pointeur vers le [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) interface.

*pColumns*<br/>
[out] Un pointeur vers la mémoire dans lequel retourner le nombre de colonnes dans l’ensemble de lignes ; Ce nombre inclut la colonne de signet, le cas échéant.

*ppColumnInfo*<br/>
[out] Pointeur vers la mémoire dans lequel retourner un tableau de `DBCOLUMNINFO` structures. Consultez la section « Structures DBCOLUMNINFO » dans [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.

*ppStringsBuffer*<br/>
[out] Pointeur vers la mémoire dans lequel retourner un pointeur vers le stockage pour toutes les valeurs de chaîne (noms utilisés au sein de *columnid* ou pour *pwszName*) au sein d’un bloc d’allocation unique.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Consultez [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *de référence du programmeur OLE DB* pour plus d’informations sur les types de données `DBORDINAL`, `DBCOLUMNINFO`, et `OLECHAR`.

## <a name="getcolumnname"></a> CDynamicAccessor::GetColumnName

Récupère le nom de la colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

### <a name="return-value"></a>Valeur de retour

Nom de la colonne spécifiée.

## <a name="getcolumntype"></a> CDynamicAccessor::GetColumnType

Récupère le type de données d’une colonne spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*pType*<br/>
[out] Pointeur vers le type de données de la colonne spécifiée.

### <a name="return-value"></a>Valeur de retour

Retourne **true** en cas de réussite ou **false** en cas d’échec.

## <a name="getlength"></a> CDynamicAccessor::GetLength

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
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

*pLength*<br/>
[out] Pointeur vers l’entier qui contient la longueur de la colonne en octets.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la colonne spécifiée est trouvée. Sinon, cette fonction retourne **false**.

### <a name="remarks"></a>Notes

Le premier remplacement prend le numéro de colonne, et les remplacements de la deuxième et troisième prennent le nom de colonne au format ANSI ou Unicode, respectivement.

## <a name="getordinal"></a> CDynamicAccessor::GetOrdinal

Récupère le numéro de colonne donné un nom de colonne.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Paramètres

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

*pOrdinal*<br/>
[out] Pointeur vers le numéro de colonne.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si une colonne portant le nom spécifié est trouvée. Sinon, cette fonction retourne **false**.

## <a name="getstatus"></a> CDynamicAccessor::GetStatus

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
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

*pStatus*<br/>
[out] Pointeur vers la variable qui contient l’état de la colonne. Consultez [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la colonne spécifiée est trouvée. Sinon, cette fonction retourne **false**.

## <a name="getvalue"></a> CDynamicAccessor::GetValue

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
[in] Un paramètre basé sur un modèle qui gère n’importe quel type de données à l’exception des types de chaîne (`CHAR*`, `WCHAR*`), qui nécessitent un traitement spécial. `GetValue` utilise le type de données approprié selon que vous spécifiez ici.

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*pColumnName*<br/>
[in] Le nom de colonne.

*pData*<br/>
[out] Pointeur vers le contenu de la colonne spécifiée.

### <a name="return-value"></a>Valeur de retour

Si vous souhaitez passer des données de chaîne, utilisez les versions non de `GetValue`. Les versions non de cette méthode retournent `void*`, qui pointe vers la partie de la mémoire tampon qui contient les données de la colonne spécifiée. Retourne NULL si la colonne est introuvable.

Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue`. Les versions basées sur un modèle retournent **true** en cas de réussite ou **false** en cas d’échec.

### <a name="remarks"></a>Notes

Utilisez les versions non pour retourner les colonnes qui contiennent des chaînes et les versions basées sur un modèle pour les colonnes qui contiennent d’autres types de données.

En mode débogage, vous obtiendrez une assertion si la taille de *pData* n’est pas égale à la taille de la colonne à laquelle il pointe.

## <a name="setblobhandling"></a> CDynamicAccessor::SetBlobHandling

Définit l’objet BLOB de valeur pour la ligne actuelle de gestion.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Paramètres

*eBlobHandling*<br/>
Spécifie la façon dont les données BLOB doit être gérée. Elle peut prendre les valeurs suivantes :

- DBBLOBHANDLING_DEFAULT : Gérer les données de colonne supérieures à *nBlobSize* (tels que définis par `SetBlobSizeLimit`) en tant que données d’objets BLOB et les récupérer via un `ISequentialStream` ou `IStream` objet. Cette option va tenter de lier chaque colonne contenant des données supérieures à *nBlobSize* ou répertorié en tant que DBTYPE_IUNKNOWN en tant que données d’objets BLOB.

- DBBLOBHANDLING_NOSTREAMS : Gérer les données de colonne supérieures à *nBlobSize* (tels que définis par `SetBlobSizeLimit`) en tant que données d’objets BLOB et les récupérer via référence dans la mémoire allouée par le fournisseur, appartenant à un consommateur. Cette option est utile pour les tables qui ont plus d’une colonne BLOB, et le fournisseur prend en charge qu’un seul `ISequentialStream` objet par l’accesseur.

- DBBLOBHANDLING_SKIP : Skip (ne pas lier) colonnes éligibles comme contenant des objets BLOB (l’accesseur ne sera pas lier ou récupérer la valeur de colonne, mais il sera toujours récupérer l’état de la colonne et la longueur).

### <a name="remarks"></a>Notes

Vous devez appeler `SetBlobHandling` avant d'appeler `Open`.

La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit l’objet BLOB de valeur à DBBLOBHANDLING_DEFAULT de gestion.

## <a name="setblobsizelimit"></a> CDynamicAccessor::SetBlobSizeLimit

Définit la taille maximale de BLOB en octets.

### <a name="syntax"></a>Syntaxe

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Paramètres

*nBlobSize*<br/>
Spécifie la limite de taille d’objet BLOB.

### <a name="remarks"></a>Notes

Définit la taille maximale de BLOB en octets ; données de colonne supérieures à cette valeur sont traitées comme un objet BLOB. Certains fournisseurs offrent des tailles très importantes pour les colonnes (par exemple, 2 Go). Plutôt que de tenter de l’allocation de mémoire pour une colonne de cette taille, vous essaierait généralement lier ces colonnes en tant qu’objets BLOB. De cette façon vous n’êtes pas obligé d’allouer toute la mémoire, mais vous pouvez toujours lire toutes les données sans craindre de troncation. Toutefois, il existe certains cas dans lequel vous pouvez souhaiter forcer `CDynamicAccessor` pour lier des colonnes volumineuses dans leurs types de données natifs. Pour ce faire, appelez `SetBlobSizeLimit` avant d’appeler `Open`.

La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit la taille maximale de BLOB pour une valeur par défaut de 8 000 octets.

## <a name="setlength"></a> CDynamicAccessor::SetLength

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
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*nLength*<br/>
[in] La longueur de la colonne en octets.

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la longueur de la colonne spécifiée est définie correctement. Sinon, cette fonction retourne **false**.

## <a name="setstatus"></a> CDynamicAccessor::SetStatus

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
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

*status*<br/>
[in] L’état de la colonne. Consultez [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si l’état de la colonne spécifiée est définie correctement. Sinon, cette fonction retourne **false**.

## <a name="setvalue"></a> CDynamicAccessor::SetValue

Stocke les données à une colonne spécifiée.

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
[in] Un paramètre basé sur un modèle qui gère n’importe quel type de données à l’exception des types de chaîne (`CHAR*`, `WCHAR*`), qui nécessitent un traitement spécial. `GetValue` utilise le type de données approprié selon que vous spécifiez ici.

*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères contenant le nom de colonne.

*data*<br/>
[in] Pointeur vers la mémoire contenant les données.

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.

### <a name="return-value"></a>Valeur de retour

Si vous souhaitez définir les données de chaîne, utilisez les versions non de `GetValue`. Les versions non de cette méthode retournent `void*`, qui pointe vers la partie de la mémoire tampon qui contient les données de la colonne spécifiée. Retourne NULL si la colonne est introuvable.

Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue`. Les versions basées sur un modèle retournent **true** en cas de réussite ou **false** en cas d’échec.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)