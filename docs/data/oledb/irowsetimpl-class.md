---
title: IRowsetImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 47b03a542933c6223e098bc9d8fa8d45bf5e047b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024450"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl, classe

Fournit une implémentation de l’interface `IRowset`.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IRowsetImpl`.

*RowsetInterface*<br/>
Une classe dérivée de `IRowsetImpl`.

*RowClass*<br/>
Unité de stockage pour le `HROW`.

*MapClass*<br/>
Unité de stockage pour tous les handles de ligne détenus par le fournisseur.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddRefRows](#addrefrows)|Ajoute un décompte de références à un handle de ligne existant.|
|[CreateRow](#createrow)|Appelé par [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) pour allouer un nouveau `HROW`. Pas appelée directement par l’utilisateur.|
|[GetData](#getdata)|Récupère les données à partir de la copie de l’ensemble de lignes de la ligne.|
|[GetDBStatus](#getdbstatus)|Retourne l’état pour le champ spécifié.|
|[GetNextRows](#getnextrows)|Extrait les lignes séquentiellement, en mémorisant la position précédente.|
|[IRowsetImpl](#irowsetimpl)|Constructeur. Pas appelée directement par l’utilisateur.|
|[RefRows](#refrows)|Appelé par [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). Pas appelée directement par l’utilisateur.|
|[ReleaseRows](#releaserows)|Libère des lignes.|
|[RestartPosition](#restartposition)|Repositionne la prochaine position d’extraction à sa position initiale ; Autrement dit, sa position lorsque l’ensemble de lignes a d’abord été créé.|
|[SetDBStatus](#setdbstatus)|Définit les indicateurs d’état pour le champ spécifié.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Indique si un fournisseur prend en charge l’extraction vers l’arrière.|
|[m_bCanScrollBack](#bcanscrollback)|Indique si un fournisseur peut avoir son défilement de curseur de vers l’arrière.|
|[m_bReset](#breset)|Indique si un fournisseur a réinitialisé à sa position de curseur. Cela a une signification spéciale lorsque le défilement vers l’arrière ou l’extraction vers l’arrière dans [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|
|[m_iRowset](#irowset)|Un index à l’ensemble de lignes, qui représente le curseur.|
|[m_rgRowHandles](#rgrowhandles)|Une liste de descripteurs de lignes.|

## <a name="remarks"></a>Notes

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) est l’interface de l’ensemble de lignes de base.

## <a name="addrefrows"></a> IRowsetImpl::AddRefRows

Ajoute un décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="createrow"></a> IRowsetImpl::CreateRow

Une méthode d’assistance appelée par [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) pour allouer un nouveau `HROW`.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>Paramètres

*lRowsOffset*<br/>
Position du curseur de la ligne en cours de création.

*cRowsObtained*<br/>
Une référence est passée à l’utilisateur qui indique le nombre de lignes créées.

*rgRows*<br/>
Un tableau de `HROW`s retourné à l’appelant avec les poignées de ligne nouvellement créée.

### <a name="remarks"></a>Notes

Si la ligne existe, cette méthode appelle [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et retourne. Sinon, il alloue une nouvelle instance de la variable de modèle RowClass et ajoute à [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).

## <a name="getdata"></a> IRowsetImpl::GetData

Récupère les données à partir de la copie de l’ensemble de lignes de la ligne.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) dans le *de référence du programmeur OLE DB*.

Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IRowset::GetData`:

|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Notes

Gère également la conversion de données à l’aide de la DLL de la conversion de données OLE DB.

## <a name="getdbstatus"></a> IRowsetImpl::GetDBStatus

Retourne les indicateurs d’état DBSTATUS pour le champ spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Paramètres

*currentRow*<br/>
[in] La ligne actuelle.

*columnNames*<br/>
[in] La colonne pour laquelle l’état est demandé.

### <a name="return-value"></a>Valeur de retour

Le [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) indicateurs de la colonne.

## <a name="getnextrows"></a> IRowsetImpl::GetNextRows

Extrait les lignes séquentiellement, en mémorisant la position précédente.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="irowsetimpl"></a> IRowsetImpl::IRowsetImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Notes

En général inutile d’appeler cette méthode directement.

## <a name="refrows"></a> IRowsetImpl::RefRows

Appelé par [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) à incrémenter ou libérer un décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="releaserows"></a> IRowsetImpl::ReleaseRows

Libère des lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="restartposition"></a> IRowsetImpl::RestartPosition

Repositionne la prochaine position d’extraction à sa position initiale ; Autrement dit, sa position lorsque l’ensemble de lignes a d’abord été créé.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset::RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

La position de l’ensemble de lignes n’est pas définie jusqu'à ce que `GetNextRow` est appelée. Vous pouvez déplacer vers l’arrière dans un rowet en appelant `RestartPosition` puis l’extraction ou le défilement vers l’arrière.

## <a name="setdbstatus"></a> IRowsetImpl::SetDBStatus

Définit les indicateurs d’état DBSTATUS pour le champ spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Paramètres

*statusFlags*<br/>
Le [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) indicateurs à définir pour la colonne.

*currentRow*<br/>
La ligne actuelle.

*columnInfo*<br/>
La colonne pour laquelle l’état est défini.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le fournisseur substitue à cette fonction pour fournir un traitement spécial pour DBSTATUS_S_ISNULL et DBSTATUS_S_DEFAULT.

## <a name="bcanfetchback"></a> IRowsetImpl::m_bCanFetchBack

Indique si un fournisseur prend en charge l’extraction vers l’arrière.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Notes

Lié à la `DBPROP_CANFETCHBACKWARDS` propriété dans le `DBPROPSET_ROWSET` groupe. Le fournisseur doit prendre en charge `DBPROP_CANFETCHBACKWARDS` pour `m_bCanFetchBackwards` être **true**.

## <a name="bcanscrollback"></a> IRowsetImpl::m_bCanScrollBack

Indique si un fournisseur peut avoir son défilement de curseur de vers l’arrière.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Notes

Lié à la `DBPROP_CANSCROLLBACKWARDS` propriété dans le `DBPROPSET_ROWSET` groupe. Le fournisseur doit prendre en charge `DBPROP_CANSCROLLBACKWARDS` pour `m_bCanFetchBackwards` être **true**.

## <a name="breset"></a> IRowsetImpl::m_bReset

Un indicateur de bit utilisé pour déterminer si la position du curseur est définie sur l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Notes

Si le consommateur appelle [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) avec une valeur négative `lOffset` ou *cRows* et `m_bReset` a la valeur true, `GetNextRows` se déplace vers la fin de l’ensemble de lignes. Si `m_bReset` a la valeur false, le consommateur reçoit un code d’erreur, conformément à la spécification OLE DB. Le `m_bReset` indicateur obtient la valeur **true** lorsque l’ensemble de lignes est tout d’abord créé et lorsque le consommateur appelle [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Elle obtient la valeur **false** lorsque vous appelez `GetNextRows`.

## <a name="irowset"></a> IRowsetImpl::m_iRowset

Un index à l’ensemble de lignes, qui représente le curseur.

### <a name="syntax"></a>Syntaxe

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="rgrowhandles"></a> IRowsetImpl::m_rgRowHandles

Un mappage de descripteurs de lignes actuellement contenus par le fournisseur en réponse à `GetNextRows`.

### <a name="syntax"></a>Syntaxe

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Notes

Handles de ligne sont supprimés en appelant `ReleaseRows`. Consultez le [vue d’ensemble de IRowsetImpl](../../data/oledb/irowsetimpl-class.md) pour la définition de *MapClass*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow, classe](../../data/oledb/csimplerow-class.md)