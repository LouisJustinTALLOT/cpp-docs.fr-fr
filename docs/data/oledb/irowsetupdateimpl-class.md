---
title: IRowsetUpdateImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 79d85e7d1c849bcaa7c2aa1b3f6d9d50a20d1b2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210312"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl, classe

Implémentation des modèles OLE DB de l’interface [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetUpdateImpl`.

*Stockage*<br/>
Enregistrement de l’utilisateur.

*UpdateArray*<br/>
Tableau contenant les données mises en cache pour la mise à jour de l’ensemble de lignes.

*RowClass*<br/>
Unité de stockage pour le `HROW`.

*MapClass*<br/>
Unité de stockage de tous les descripteurs de lignes détenues par le fournisseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisées avec IRowsetChange)

|||
|-|-|
|[SetData](#setdata)|Définit des valeurs de données dans une ou plusieurs colonnes.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Méthodes d’interface (utilisées avec IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Obtient les données les plus récemment transmises à la source de données ou obtenues de celle-ci, en ignorant les modifications en attente.|
|[GetPendingRows](#getpendingrows)|Retourne une liste de lignes avec des modifications en attente.|
|[GetRowStatus](#getrowstatus)|Retourne l’état des lignes spécifiées.|
|[Annuler](#undo)|Annule toutes les modifications apportées à la ligne depuis la dernière extraction ou mise à jour.|
|[Mettre à jour](#update)|Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou mise à jour.|

### <a name="implementation-methods-callback"></a>Méthodes d’implémentation (rappel)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Utilisé pour vérifier la sécurité, l’intégrité, etc. avant d’autoriser les mises à jour.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Contient les données d’origine pour l’opération différée.|

## <a name="remarks"></a>Notes

Vous devez d’abord lire et comprendre la documentation de [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), car tous les éléments qui y sont décrits s’appliquent également ici. Vous devez également lire le chapitre 6 du *OLE DB Guide de référence du programmeur* sur le paramétrage des données.

`IRowsetUpdateImpl` implémente l’interface `IRowsetUpdate` OLE DB, qui permet aux consommateurs de retarder la transmission des modifications effectuées avec `IRowsetChange` à la source de données et d’annuler les modifications avant la transmission.

> [!IMPORTANT]
>  Nous vous recommandons vivement de lire la documentation suivante avant d’essayer d’implémenter votre fournisseur :

- [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)

- Chapitre 6 du *Guide de référence du programmeur OLE DB*

- Découvrez également comment la classe `RUpdateRowset` est utilisée dans l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl :: SetData

Définit des valeurs de données dans une ou plusieurs colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetChange :: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Cette méthode remplace la méthode [IRowsetChangeImpl :: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) , mais elle comprend la mise en cache des données d’origine pour autoriser le traitement immédiat ou différé de l’opération.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl :: GetOriginalData

Obtient les données les plus récemment transmises à la source de données ou obtenues de celle-ci, en ignorant les modifications en attente.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetUpdate :: GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl :: GetPendingRows

Retourne une liste de lignes avec des modifications en attente.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Paramètres

*hReserved*<br/>
dans Correspond au paramètre *hChapter* dans [IRowsetUpdate :: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetUpdate :: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IRowsetUpdate :: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl :: GetRowStatus

Retourne l’état des lignes spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Paramètres

*hReserved*<br/>
dans Correspond au paramètre *hChapter* dans [IRowsetUpdate :: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetUpdate :: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl :: Undo

Annule toutes les modifications apportées à la ligne depuis la dernière extraction ou mise à jour.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Paramètres

*hReserved*<br/>
dans Correspond au paramètre *hChapter* dans [IRowsetUpdate :: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
à Correspond au paramètre *pcRows* dans [IRowsetUpdate :: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
dans Correspond au paramètre *prgRows* dans [IRowsetUpdate :: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetUpdate :: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl :: Update

Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou mise à jour.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Paramètres

*hReserved*<br/>
dans Correspond au paramètre *hChapter* dans [IRowsetUpdate :: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Pour les autres paramètres, consultez [IRowsetUpdate :: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Les modifications sont transmises en appelant [IRowsetChangeImpl :: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Le consommateur doit appeler [CRowset :: Update](../../data/oledb/crowset-update.md) pour que les modifications prennent effet. Affectez une valeur appropriée à *prgRowstatus* , comme décrit dans les [États de ligne](/previous-versions/windows/desktop/ms722752(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl :: IsUpdateAllowed

Remplacez cette méthode pour vérifier la sécurité, l’intégrité, etc. avant les mises à jour.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Paramètres

*statut*<br/>
dans État des opérations en attente sur les lignes.

*hRowUpdate*<br/>
dans Handle pour les lignes que l’utilisateur souhaite mettre à jour.

*pRowStatus*<br/>
à État renvoyé à l’utilisateur.

### <a name="remarks"></a>Notes

Si vous déterminez qu’une mise à jour doit être autorisée, retourne S_OK ; Sinon, Retourne E_FAIL. Si vous autorisez une mise à jour, vous devez également définir le `DBROWSTATUS` dans [IRowsetUpdateImpl :: Update](../../data/oledb/irowsetupdateimpl-update.md) sur un [État de ligne](/previous-versions/windows/desktop/ms722752(v=vs.85))approprié.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl :: m_mapCachedData

Mappage contenant les données d’origine pour l’opération différée.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Paramètres

*Fère*<br/>
Handle vers les lignes pour les données.

*pData*<br/>
Pointeur vers les données à mettre en cache. Les données sont de type *stockage* (classe enregistrement utilisateur). Consultez l’argument de modèle de *stockage* dans la [classe IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)
