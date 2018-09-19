---
title: IRowsetUpdateImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
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
- GetRowStatus
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 67510ada7af557877f427d757200a48c0df95fe9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054114"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl, classe

L’implémentation de modèles OLE DB de la [IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\)) interface.  
  
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
Une classe dérivée de `IRowsetUpdateImpl`.  
  
*Stockage*<br/>
L’enregistrement utilisateur.  
  
*UpdateArray*<br/>
Tableau contenant les données mises en cache pour la mise à jour de l’ensemble de lignes.  
  
*RowClass*<br/>
L’unité de stockage pour le `HROW`.  
  
*MapClass*<br/>
L’unité de stockage pour tous les handles de ligne détenus par le fournisseur.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisés avec IRowsetChange)  
  
|||  
|-|-|  
|[SetData](#setdata)|Définit les valeurs de données dans une ou plusieurs colonnes.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Méthodes d’interface (utilisés avec IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|Obtient les données récemment transmises à ou obtenu à partir de la source de données, en ignorant les modifications en attente.|  
|[GetPendingRows](#getpendingrows)|Retourne une liste de lignes avec des modifications en attente.|  
|[GetRowStatus](#getrowstatus)|Retourne l’état des lignes spécifiées.|  
|[Annulation](#undo)|Annule les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.|  
|[Mettre à jour](#update)|Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.|  
  
### <a name="implementation-methods-callback"></a>Méthodes d’implémentation (rappel)  
  
|||  
|-|-|  
|[IsUpdateAllowed](#isupdateallowed)|Utilisé pour contrôler la sécurité, l’intégrité, et ainsi de suite avant d’autoriser les mises à jour.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|Contient les données d’origine pour l’opération différée.|  
  
## <a name="remarks"></a>Notes  

Vous devez tout d’abord lire et comprendre sa documentation [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)), car toutes les procédures décrites il s’applique également ici. Vous devez également lire le chapitre 6 de la *de référence du programmeur OLE DB* sur la définition de données.  
  
`IRowsetUpdateImpl` implémente la norme OLE DB `IRowsetUpdate` interface, ce qui permet aux consommateurs de retarder la transmission des modifications apportées avec `IRowsetChange` à source de données et annuler les modifications avant la transmission.  
  
> [!IMPORTANT]
>  Il est fortement recommandé que vous lire la documentation suivante avant de tenter d’implémenter votre fournisseur :  
  
- [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)  
  
- Chapitre 6 de la *de référence du programmeur OLE DB*  
  
- Consultez également comment la `RUpdateRowset` classe est utilisée dans le [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) exemple  

## <a name="setdata"></a> IRowsetUpdateImpl::SetData

Définit les valeurs de données dans une ou plusieurs colonnes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Cette méthode remplace la [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) (méthode), mais il inclut la mise en cache des données d’origine pour permettre le traitement immédiat ou différé de l’opération.

## <a name="getoriginaldata"></a> IRowsetUpdateImpl::GetOriginalData

Obtient les données récemment transmises à ou obtenu à partir de la source de données, en ignorant les modifications en attente.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.   

## <a name="getpendingrows"></a> IRowsetUpdateImpl::GetPendingRows

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
[in] Correspond à la *hChapter* paramètre dans [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Pour plus d’informations, consultez [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="getrowstatus"></a> IRowsetUpdateImpl::GetRowStatus

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
[in] Correspond à la *hChapter* paramètre dans [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="undo"></a> IRowsetUpdateImpl::Undo

Annule les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.  
  
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
[in] Correspond à la *hChapter* paramètre dans [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
*pcRowsUndone*<br/>
[out] Correspond à la *pcRows* paramètre dans [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
*prgRowsUndone*<br/>
[in] Correspond à la *prgRows* paramètre dans [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)) dans le *de référence du programmeur OLE DB*. 

## <a name="update"></a> IRowsetUpdateImpl::Update

Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.  
  
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
[in] Correspond à la *hChapter* paramètre dans [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709\(v=vs.85\)).  
  
Pour les autres paramètres, consultez [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Les modifications sont transmises en appelant [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Le consommateur doit appeler [CRowset::Update](../../data/oledb/crowset-update.md) pour que les modifications entrent en vigueur. Définissez *prgRowstatus* à une valeur appropriée, comme décrit dans [États des lignes](/previous-versions/windows/desktop/ms722752\(v=vs.85\)) dans le *de référence du programmeur OLE DB*. 
  
## <a name="isupdateallowed"></a> IRowsetUpdateImpl::IsUpdateAllowed

Substituez cette méthode pour contrôler la sécurité, l’intégrité, et ainsi de suite avant les mises à jour.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Paramètres  

*status*<br/>
[in] L’état des opérations sur les lignes en attente.  
  
*hRowUpdate*<br/>
[in] Handle pour les lignes que l’utilisateur souhaite mettre à jour.  
  
*pRowStatus*<br/>
[out] L’état renvoyé à l’utilisateur.  
  
### <a name="remarks"></a>Notes  

Si vous déterminez qu’une mise à jour doit être autorisé, retourne S_OK ; Sinon, retourne E_FAIL. Si vous autorisez une mise à jour, vous devez également définir le `DBROWSTATUS` dans [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) un appropriés [état de la ligne](/previous-versions/windows/desktop/ms722752\(v=vs.85\)).  

## <a name="mapcacheddata"></a> IRowsetUpdateImpl::m_mapCachedData

Un mappage qui contient les données d’origine pour l’opération différée.  
  
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
Handle vers les lignes pour les données.  
  
*pData*<br/>
Un pointeur vers les données à mettre en cache. Les données sont de type *stockage* (la classe d’enregistrement utilisateur). Consultez le *stockage* argument template dans [IRowsetUpdateImpl, classe](../../data/oledb/irowsetupdateimpl-class.md).  

## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)