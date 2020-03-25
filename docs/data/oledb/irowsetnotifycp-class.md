---
title: IRowsetNotifyCP, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: fa85bc7947b3b446ec7c6d3fdb0d7b62d308fb53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210325"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP, classe

Implémente le site du fournisseur pour l’interface de point de connexion [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

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

*T*<br/>
Classe dérivée de `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Classe Mutex qui prend en charge la réentrance (la valeur par défaut est `CComSharedMutex`). Un mutex est un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.

*piid*<br/>
Pointeur d’ID d’interface (`IID*`) pour une interface de point de connexion `IRowsetNotify`. La valeur par défaut est `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
Tableau de type [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), qui est un tableau alloué dynamiquement de pointeurs `IUnknown` vers les interfaces du récepteur client.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Notifie le consommateur d’une modification de la valeur d’une colonne.|
|[Fire_OnRowChange](#onrowchange)|Notifie le consommateur d’une modification affectant les lignes.|
|[Fire_OnRowsetChange](#onrowsetchange)|Notifie le consommateur d’une modification affectant l’ensemble de lignes entier.|

## <a name="remarks"></a>Notes

`IRowsetNotifyCP` implémente des fonctions de diffusion pour informer les écouteurs sur le point de connexion `IID_IRowsetNotify` des modifications apportées au contenu de l’ensemble de lignes.

Notez que vous devez également implémenter et inscrire `IRowsetNotify` sur le consommateur (également appelé « récepteur ») à l’aide de [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) afin que le consommateur puisse gérer les notifications. Consultez [réception de notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.

Pour plus d’informations sur l’implémentation des notifications, consultez « notifications de prise en charge » dans [création d’un fournisseur pouvant être mis à jour](../../data/oledb/creating-an-updatable-provider.md).

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyCP :: Fire_OnFieldChange

Diffuse un événement [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour informer les utilisateurs d’une modification de la valeur d’une colonne.

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

Consultez [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a>IRowsetNotifyCP :: Fire_OnRowChange

Diffuse un événement [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) à tous les écouteurs sur le point de connexion `IID_IRowsetNotify` pour informer les utilisateurs d’une modification affectant les lignes.

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

Consultez [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyCP :: Fire_OnRowsetChange

Diffuse un événement [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) à tous les écouteurs sur le point de connexion `IID_IRowsetNotify` pour informer les consommateurs d’une modification affectant l’ensemble de lignes entier.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Notifications (COM)](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)
