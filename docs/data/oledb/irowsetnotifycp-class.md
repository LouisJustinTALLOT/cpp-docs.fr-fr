---
title: IRowsetNotifyCP, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 207128da3e46da492ebc812b68d9ef09847045e5
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322122"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP, classe
Implémente le site du fournisseur pour l’interface de point de connexion [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Une classe dérivée de `IRowsetNotifyCP`.  
  
 *ReentrantEventSync*  
 Une classe de mutex qui prend en charge de la réentrance (la valeur par défaut est `CComSharedMutex`). Un mutex est un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.  
  
 *piid*  
 Un pointeur d’interface ID (`IID*`) pour un `IRowsetNotify` interface point de connexion. La valeur par défaut est `&__uuidof(IRowsetNotify)`.  
  
 *DynamicUnkArray*  
 Tableau de type [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), qui est un tableau alloué dynamiquement de `IUnknown` interfaces de récepteur de pointeurs vers le client. 

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h   
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Fire_OnFieldChange](#onfieldchange)|Notifie le consommateur d’une modification à la valeur d’une colonne.|  
|[Fire_OnRowChange](#onrowchange)|Notifie le consommateur d’une modification qui affectent les lignes.|  
|[Fire_OnRowsetChange](#onrowsetchange)|Notifie le consommateur d’une modification qui affectent l’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 `IRowsetNotifyCP` implémente des fonctions pour informer les écouteurs sur le point de connexion de diffusion `IID_IRowsetNotify` des modifications apportées au contenu de l’ensemble de lignes.  
  
 Notez que vous devez également implémenter et inscrire `IRowsetNotify` sur le consommateur (également appelé « sink ») à l’aide de [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) afin que le consommateur peut gérer les notifications. Consultez [réception des Notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.  
  
 Pour plus d’informations sur l’implémentation des notifications, consultez « Prise en charge des Notifications » dans [création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md).  

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange
Diffuse un [OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) événement pour avertir les utilisateurs d’une modification à la valeur d’une colonne.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,  
   HROW hRow,  
   DBORDINAL cColumns,  
   DBORDINAL* rgColumns,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange
Diffuse un [OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) événement à tous les écouteurs sur le point de connexion `IID_IRowsetNotify` pour avertir les utilisateurs d’une modification qui affectent les lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) dans le *de référence du programmeur OLE DB*.  

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange
Diffuse un [OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) événement à tous les écouteurs sur le point de connexion `IID_IRowsetNotify` pour avertir les utilisateurs d’une modification qui affectent l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) dans le *de référence du programmeur OLE DB*.
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Notifications (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)
