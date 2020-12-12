---
description: 'En savoir plus sur : classe IRowsetNotifyImpl'
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
ms.openlocfilehash: e07f918d7315998f5aa0dc14dbd613520a68f134
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287045"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl, classe

Implémente et inscrit [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) sur le consommateur (également appelé « récepteur ») afin qu’il puisse gérer les notifications.

## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[OnFieldChange](#onfieldchange)|Notifie le consommateur de toute modification apportée à la valeur d'une colonne.|
|[OnRowChange](#onrowchange)|Notifie le consommateur de la première modification apportée à une ligne ou de toute modification qui affecte la ligne entière.|
|[OnRowsetChange](#onrowsetchange)|Notifie le consommateur de toute modification qui affecte le jeu de lignes entier.|

## <a name="remarks"></a>Notes

Consultez [réception de notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.

`IRowsetNotifyImpl` fournit une implémentation factice pour `IRowsetNotify` , avec des fonctions vides pour les `IRowsetNotify` méthodes [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))et [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). Si vous héritez de cette classe lorsque vous implémentez une `IRowsetNotify` interface, vous pouvez implémenter uniquement les méthodes dont vous avez besoin. Vous devez également fournir des implémentations vides pour les autres méthodes.

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyImpl :: OnFieldChange

Notifie le consommateur de toute modification apportée à la valeur d'une colonne.

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

### <a name="return-value"></a>Valeur renvoyée

Consultez [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a> IRowsetNotifyImpl :: OnRowChange

Notifie le consommateur de la première modification apportée à une ligne ou de toute modification qui affecte la ligne entière.

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

### <a name="return-value"></a>Valeur renvoyée

Consultez [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyImpl :: OnRowsetChange

Notifie le consommateur de toute modification qui affecte le jeu de lignes entier.

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

### <a name="return-value"></a>Valeur renvoyée

Consultez [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) pour obtenir les descriptions des valeurs de retour.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode [IRowsetNotify :: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) . Pour plus d’informations, consultez la description de cette méthode dans le Guide de référence du programmeur OLE DB.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
 [IRowsetNotifyCP, classe](../../data/oledb/irowsetnotifycp-class.md)
