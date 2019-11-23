---
title: IRowsetNotifyImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: 4e6b4c3298c063038e7365496f26f50d3789be86
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311707"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl, classe

Implémente et inscrit [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) sur le consommateur (également appelé « récepteur ») afin qu’il puisse gérer les notifications.

## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[OnFieldChange](#onfieldchange)|Notifie le consommateur de toute modification apportée à la valeur d’une colonne.|
|[OnRowChange](#onrowchange)|Notifie le consommateur de la première modification apportée à une ligne ou à toute modification qui affecte la ligne entière.|
|[OnRowsetChange](#onrowsetchange)|Notifie le consommateur de toute modification affectant l’ensemble de lignes entier.|

## <a name="remarks"></a>Notes

Consultez [réception de notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.

`IRowsetNotifyImpl` fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour les méthodes `IRowsetNotify` [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))et [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). Si vous héritez de cette classe lorsque vous implémentez une interface `IRowsetNotify`, vous pouvez implémenter uniquement les méthodes dont vous avez besoin. Vous devez également fournir des implémentations vides pour les autres méthodes.

## <a name="onfieldchange"></a>IRowsetNotifyImpl :: OnFieldChange

Notifie le consommateur de toute modification apportée à la valeur d’une colonne.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour obtenir la description des paramètres.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="onrowchange"></a>IRowsetNotifyImpl :: OnRowChange

Notifie le consommateur de la première modification apportée à une ligne ou à toute modification qui affecte la ligne entière.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) pour obtenir la description des paramètres.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="onrowsetchange"></a>IRowsetNotifyImpl :: OnRowsetChange

Notifie le consommateur de toute modification affectant l’ensemble de lignes entier.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) pour obtenir la description des paramètres.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP, classe](../../data/oledb/irowsetnotifycp-class.md)
