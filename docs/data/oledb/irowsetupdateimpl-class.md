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
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370745"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl, classe

L’implémentation OLE DB Templates de l’interface [IRowsetUpdate.](/previous-versions/windows/desktop/ms714401(v=vs.85))

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
Une classe `IRowsetUpdateImpl`dérivée de .

*Stockage*<br/>
L’enregistrement de l’utilisateur.

*Mise à jourArray*<br/>
Un tableau contenant des données mises en cache pour la mise à jour du rowset.

*Classe Row*<br/>
L’unité de `HROW`stockage pour le .

*MapClass (en)*<br/>
L’unité de stockage pour toutes les poignées de ligne détenues par le fournisseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisé avec IRowsetChange)

|||
|-|-|
|[Setdata](#setdata)|Définit les valeurs de données dans une ou plusieurs colonnes.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Méthodes d’interface (utilisé avec IRowsetUpdate)

|||
|-|-|
|[GetOriginalData (en anglais seulement)](#getoriginaldata)|Obtient les données les plus récentes transmises à la source de données ou obtenues, ignorant les changements en attente.|
|[GetPendingRows GetPendingRows GetPendingRows GetPending](#getpendingrows)|Retourne une liste de lignes avec des changements en attente.|
|[GetRowStatus GetRowStatus](#getrowstatus)|Retourne l’état des lignes spécifiées.|
|[Annuler](#undo)|Annule tout changement à la ligne depuis la dernière mise à jour.|
|[Mettre à jour](#update)|Transmet toutes les modifications apportées à la ligne depuis la dernière mise à jour.|

### <a name="implementation-methods-callback"></a>Méthodes de mise en œuvre (Rappel)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Utilisé pour vérifier la sécurité, l’intégrité, et ainsi de suite avant d’autoriser les mises à jour.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Contient les données d’origine pour l’opération différée.|

## <a name="remarks"></a>Notes

Vous devriez d’abord lire et comprendre la documentation pour [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), parce que tout ce décrit là s’applique également ici. Vous devez également lire le chapitre 6 de la *référence du programmeur OLE DB* sur le réglage des données.

`IRowsetUpdateImpl`implémente l’interface OLE DB, `IRowsetUpdate` qui permet `IRowsetChange` aux consommateurs de retarder la transmission des modifications apportées à la source de données et d’annuler les modifications avant la transmission.

> [!IMPORTANT]
> Il est fortement recommandé que vous lisiez la documentation suivante AVANT de tenter de mettre en œuvre votre fournisseur :

- [Création d’un fournisseur Updatable](../../data/oledb/creating-an-updatable-provider.md)

- Chapitre 6 de la *référence du programmeur OLE DB*

- Voir aussi `RUpdateRowset` comment la classe est utilisée dans l’échantillon [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl::SetData

Définit les valeurs de données dans une ou plusieurs colonnes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Paramètres

Voir [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in the *OLE DB Programmer’s Reference*.

### <a name="remarks"></a>Notes

Cette méthode remplace la méthode [IRowsetChangeImpl::SetData,](../../data/oledb/irowsetchangeimpl-setdata.md) mais comprend la mise en cache de données originales pour permettre le traitement immédiat ou différé de l’opération.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData IRowsetUpdateImpl::GetOriginalData

Obtient les données les plus récentes transmises à la source de données ou obtenues, ignorant les changements en attente.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Paramètres

Voir [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl::GetPendingRows IRowsetUpdateImpl::GetPendingRows IRowsetUpdateImpl::GetPendingRows IRow

Retourne une liste de lignes avec des changements en attente.

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
[dans] Correspond au paramètre *hChapter* dans [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Pour d’autres paramètres, voir [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) in the *OLE DB Programmer’s Reference*.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl::GetRowStatus

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
[dans] Correspond au paramètre *hChapter* dans [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Pour d’autres paramètres, voir [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) dans la *référence du programmeur OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl::Undo

Annule tout changement à la ligne depuis la dernière mise à jour.

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
[dans] Correspond au paramètre *hChapter* dans [IRowsetUpdate:Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone (en anglais)*<br/>
[out] Correspond au paramètre *pcRows* dans [IRowsetUpdate:Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[dans] Correspond au *paramètre prgRows* dans [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Pour d’autres paramètres, voir [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) in the *OLE DB Programmer’s Reference*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl::Mise à jour

Transmet toutes les modifications apportées à la ligne depuis la dernière mise à jour.

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
[dans] Correspond au paramètre *hChapter* dans [IRowsetUpdate::Mise à jour](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Pour d’autres paramètres, voir [IRowsetUpdate::Mise à jour](/previous-versions/windows/desktop/ms719709(v=vs.85)) dans la *référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Les changements sont transmis en appelant [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Le consommateur doit appeler [CRowset::Mise](../../data/oledb/crowset-update.md) à jour pour que les modifications prennent effet. Définissez *prgRowstatus* à une valeur appropriée telle que décrite dans [les États de ligne](/previous-versions/windows/desktop/ms722752(v=vs.85)) dans la référence du *programmeur OLE DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed

Remplacez cette méthode pour vérifier la sécurité, l’intégrité, et ainsi de suite avant les mises à jour.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Paramètres

*statut*<br/>
[dans] L’état des opérations en cours sur les rangées.

*hRowUpdate (en)*<br/>
[dans] Poignée pour les lignes que l’utilisateur veut mettre à jour.

*pRowStatus*<br/>
[out] Le statut est retourné à l’utilisateur.

### <a name="remarks"></a>Notes

Si vous déterminez qu’une mise à jour doit être autorisée, les retours S_OK; E_FAIL retourne autrement. Si vous autorisez une mise à `DBROWSTATUS` jour, vous devez également définir le dans [IRowsetUpdateImpl::Mise](../../data/oledb/irowsetupdateimpl-update.md) à jour à un [état de ligne](/previous-versions/windows/desktop/ms722752(v=vs.85))approprié .

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData

Une carte contenant les données originales pour l’opération différée.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Paramètres

*hRow*<br/>
Gérer les lignes pour les données.

*Pdata*<br/>
Un pointeur sur les données à mettre en cache. Les données sont de type *Stockage* (la classe d’enregistrement utilisateur). Voir l’argument du modèle *de stockage* dans [IRowsetUpdateImpl Class](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Création d’un fournisseur Updatable](../../data/oledb/creating-an-updatable-provider.md)
