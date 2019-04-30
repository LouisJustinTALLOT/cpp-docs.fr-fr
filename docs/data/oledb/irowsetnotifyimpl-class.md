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
ms.openlocfilehash: 552fcdcee99f1bfe78a28c6ea41a89557f1682f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390698"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl, classe

Implémente et enregistre [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) sur le consommateur (également appelé « sink ») afin qu’il puisse gérer les notifications.

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
|[OnRowChange](#onrowchange)|Notifie le consommateur de la première modification à une ligne ou de toute modification qui affecte la ligne entière.|
|[OnRowsetChange](#onrowsetchange)|Notifie le consommateur de toute modification qui affecte l’ensemble de lignes.|

## <a name="remarks"></a>Notes

Consultez [réception des Notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.

`IRowsetNotifyImpl` Fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour le `IRowsetNotify` méthodes [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)), et [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). Si vous héritez de cette classe lorsque vous implémentez un `IRowsetNotify` interface, vous pouvez implémenter uniquement les méthodes que vous avez besoin. Vous devez également fournir des implémentations vides pour les autres méthodes vous-même.

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange

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

Consultez [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour obtenir des descriptions de paramètre.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour des descriptions de la valeur de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule le [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) (méthode). Consultez la description de cette méthode dans la référence du programmeur OLE DB pour plus d’informations.

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange

Notifie le consommateur de la première modification à une ligne ou de toute modification qui affecte la ligne entière.

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

Consultez [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) pour obtenir des descriptions de paramètre.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) pour des descriptions de la valeur de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule le [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) (méthode). Consultez la description de cette méthode dans la référence du programmeur OLE DB pour plus d’informations.

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange

Notifie le consommateur de toute modification qui affecte l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) pour obtenir des descriptions de paramètre.

### <a name="return-value"></a>Valeur de retour

Consultez [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) pour des descriptions de la valeur de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule le [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) (méthode). Consultez la description de cette méthode dans la référence du programmeur OLE DB pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP, classe](../../data/oledb/irowsetnotifycp-class.md)