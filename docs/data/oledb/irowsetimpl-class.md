---
title: IRowsetImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
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
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
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
ms.openlocfilehash: 470755744783272245ca3aa8e4b57e2943db5fae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840399"
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
Votre classe, dérivée de `IRowsetImpl` .

*RowsetInterface*<br/>
Classe dérivée de `IRowsetImpl` .

*RowClass*<br/>
Unité de stockage pour le `HROW` .

*MapClass*<br/>
Unité de stockage pour tous les handles de ligne détenus par le fournisseur.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddRefRows](#addrefrows)|Ajoute un décompte de références à un handle de ligne existant.|
|[CreateRow](#createrow)|Appelé par [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) pour allouer un nouveau `HROW` . Non appelé directement par l’utilisateur.|
|[GetData](#getdata)|Récupère des données de la copie du jeu de lignes de la ligne.|
|[GetDBStatus](#getdbstatus)|Retourne l’état du champ spécifié.|
|[GetNextRows](#getnextrows)|Extrait des lignes séquentiellement, en mémorisant la position précédente.|
|[IRowsetImpl](#irowsetimpl)|Constructeur. Non appelé directement par l’utilisateur.|
|[RefRows](#refrows)|Appelée par [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). Non appelé directement par l’utilisateur.|
|[ReleaseRows](#releaserows)|Libère des lignes.|
|[RestartPosition](#restartposition)|Repositionne la position d’extraction suivante à sa position initiale ; autrement dit, sa position lors de la création de l’ensemble de lignes.|
|[SetDBStatus](#setdbstatus)|Définit les indicateurs d’État pour le champ spécifié.|

### <a name="data-members"></a>Données membres

| Nom | Description |
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Indique si un fournisseur prend en charge l’extraction vers l’arrière.|
|[m_bCanScrollBack](#bcanscrollback)|Indique si un fournisseur peut faire défiler le curseur vers l’arrière.|
|[m_bReset](#breset)|Indique si un fournisseur a réinitialisé sa position de curseur. Cela a une signification particulière lors du défilement vers l’arrière ou de l’extraction vers l’arrière dans [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|
|[m_iRowset](#irowset)|Index de l’ensemble de lignes, représentant le curseur.|
|[m_rgRowHandles](#rgrowhandles)|Liste de handles de ligne.|

## <a name="remarks"></a>Notes

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) est l’interface de l’ensemble de lignes de base.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a> IRowsetImpl :: AddRefRows

Ajoute un décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset :: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a> IRowsetImpl :: CreateRow

Méthode d’assistance appelée par [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) pour allouer une nouvelle `HROW` .

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
Référence retournée à l’utilisateur indiquant le nombre de lignes créées.

*rgRows*<br/>
Tableau d’objets `HROW` retournés à l’appelant avec les descripteurs de ligne nouvellement créés.

### <a name="remarks"></a>Notes

Si la ligne existe, cette méthode appelle [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et retourne. Dans le cas contraire, il alloue une nouvelle instance de la variable de modèle RowClass et l’ajoute à [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).

## <a name="irowsetimplgetdata"></a><a name="getdata"></a> IRowsetImpl :: GetData

Récupère des données de la copie du jeu de lignes de la ligne.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset :: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

Certains paramètres correspondent à *OLE DB paramètres de référence du programmeur* de différents noms, qui sont décrits dans `IRowset::GetData` :

|Paramètres du modèle de OLE DB|Paramètres *de référence du programmeur OLE DB*|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Notes

Gère également la conversion de données à l’aide de la DLL de conversion de données OLE DB.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a> IRowsetImpl :: GetDBStatus

Retourne les indicateurs d’État DBSTATUS pour le champ spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Paramètres

*currentRow*<br/>
dans Ligne actuelle.

*columnNames*<br/>
dans Colonne pour laquelle l’État est demandé.

### <a name="return-value"></a>Valeur renvoyée

Indicateurs [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) pour la colonne.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a> IRowsetImpl :: GetNextRows

Extrait des lignes séquentiellement, en mémorisant la position précédente.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset :: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a> IRowsetImpl :: IRowsetImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Notes

En général, vous n’avez pas besoin d’appeler cette méthode directement.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a> IRowsetImpl :: RefRows

Appelée par [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) et [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) pour incrémenter ou libérer un décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset :: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a> IRowsetImpl :: ReleaseRows

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

Consultez [IRowset :: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a> IRowsetImpl :: RestartPosition

Repositionne la position d’extraction suivante à sa position initiale ; autrement dit, sa position lors de la création de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowset :: RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

La position de l’ensemble de lignes n’est pas définie tant que `GetNextRow` n’est pas appelé. Vous pouvez revenir en arrière dans un rowet en appelant `RestartPosition` , puis en extrayant ou en faisant défiler vers l’arrière.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a> IRowsetImpl :: SetDBStatus

Définit les indicateurs d’État DBSTATUS pour le champ spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Paramètres

*statusFlags*<br/>
Indicateurs [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) à définir pour la colonne.

*currentRow*<br/>
La ligne actuelle.

*columnInfo*<br/>
Colonne pour laquelle l’État est défini.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le fournisseur remplace cette fonction pour fournir un traitement spécial pour DBSTATUS_S_ISNULL et DBSTATUS_S_DEFAULT.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a> IRowsetImpl :: m_bCanFetchBack

Indique si un fournisseur prend en charge l’extraction vers l’arrière.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Notes

Lié à la `DBPROP_CANFETCHBACKWARDS` propriété dans le `DBPROPSET_ROWSET` groupe. Le fournisseur doit prendre en charge pour que la `DBPROP_CANFETCHBACKWARDS` `m_bCanFetchBackwards` valeur soit **`true`** .

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a> IRowsetImpl :: m_bCanScrollBack

Indique si un fournisseur peut faire défiler le curseur vers l’arrière.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Notes

Lié à la `DBPROP_CANSCROLLBACKWARDS` propriété dans le `DBPROPSET_ROWSET` groupe. Le fournisseur doit prendre en charge pour que la `DBPROP_CANSCROLLBACKWARDS` `m_bCanFetchBackwards` valeur soit **`true`** .

## <a name="irowsetimplm_breset"></a><a name="breset"></a> IRowsetImpl :: m_bReset

Indicateur binaire utilisé pour déterminer si la position du curseur est définie sur l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Notes

Si le consommateur appelle [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) avec un négatif `lOffset` ou en *pattes* et `m_bReset` s’il a la valeur true, `GetNextRows` se déplace à la fin de l’ensemble de lignes. Si `m_bReset` a la valeur false, le consommateur reçoit un code d’erreur, en conformité avec la spécification OLE DB. L' `m_bReset` indicateur obtient la valeur **`true`** lorsque l’ensemble de lignes est créé pour la première fois et lorsque le consommateur appelle [IRowsetImpl :: RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Il obtient la valeur **`false`** lorsque vous appelez `GetNextRows` .

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a> IRowsetImpl :: m_iRowset

Index de l’ensemble de lignes, représentant le curseur.

### <a name="syntax"></a>Syntaxe

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a> IRowsetImpl :: m_rgRowHandles

Mappage de handles de ligne actuellement contenus par le fournisseur en réponse à `GetNextRows` .

### <a name="syntax"></a>Syntaxe

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Notes

Les handles de ligne sont supprimés en appelant `ReleaseRows` . Consultez la [vue d’ensemble de IRowsetImpl](../../data/oledb/irowsetimpl-class.md) pour la définition de *MapClass*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow, classe](../../data/oledb/csimplerow-class.md)
