---
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
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496939"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent, classe

Cette classe fournit des méthodes pour notifier le récepteur du conteneur en ce qui concerne les modifications des propriétés de contrôle.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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

`CFirePropNotifyEvent`a deux méthodes qui notifient le récepteur du conteneur qu’une propriété de contrôle a été modifiée ou est sur le paragraphe de changer.

Si la classe qui implémente votre contrôle est `IPropertyNotifySink`dérivée `CFirePropNotifyEvent` de, les méthodes sont appelées `FireOnRequestEdit` lorsque `FireOnChanged`vous appelez ou. Si votre classe de contrôle n’est pas `IPropertyNotifySink`dérivée de, les appels à ces fonctions retournent S_OK.

Pour plus d’informations sur la création de contrôles, consultez le [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

Avertit toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété d’objet spécifiée a changé.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers le `IUnknown` de l’objet qui envoie la notification.

*dispID*<br/>
dans Identificateur de la propriété qui a changé.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

Avertit toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété d’objet spécifiée est sur le point de changer.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers le `IUnknown` de l’objet qui envoie la notification.

*dispID*<br/>
dans Identificateur de la propriété à modifier.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
