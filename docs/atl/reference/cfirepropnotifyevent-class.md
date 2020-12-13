---
description: 'En savoir plus sur : classe CFirePropNotifyEvent'
title: CFirePropNotifyEvent, classe
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 09102e67408195751e083807f444c1b028fd2762
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141724"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent, classe

Cette classe fournit des méthodes pour notifier le récepteur du conteneur en ce qui concerne les modifications des propriétés de contrôle.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|Statique Notifie le récepteur du conteneur qu’une propriété de contrôle a été modifiée.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|Statique Notifie le récepteur du conteneur qu’une propriété de contrôle va être modifiée.|

## <a name="remarks"></a>Notes

`CFirePropNotifyEvent` a deux méthodes qui notifient le récepteur du conteneur qu’une propriété de contrôle a été modifiée ou est sur le paragraphe de changer.

Si la classe qui implémente votre contrôle est dérivée de `IPropertyNotifySink` , les `CFirePropNotifyEvent` méthodes sont appelées lorsque vous appelez `FireOnRequestEdit` ou `FireOnChanged` . Si votre classe de contrôle n’est pas dérivée de `IPropertyNotifySink` , les appels à ces fonctions retournent S_OK.

Pour plus d’informations sur la création de contrôles, consultez le [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a> CFirePropNotifyEvent::FireOnChanged

Avertit toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété d’objet spécifiée a changé.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers le `IUnknown` de l’objet qui envoie la notification.

*Égal*<br/>
dans Identificateur de la propriété qui a changé.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a> CFirePropNotifyEvent::FireOnRequestEdit

Avertit toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété d’objet spécifiée est sur le point de changer.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers le `IUnknown` de l’objet qui envoie la notification.

*Égal*<br/>
dans Identificateur de la propriété à modifier.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
