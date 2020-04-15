---
title: Classe CFirePropNotifyEvent
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
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326972"
---
# <a name="cfirepropnotifyevent-class"></a>Classe CFirePropNotifyEvent

Cette classe fournit des méthodes pour aviser l’évier du conteneur concernant les changements de propriété de contrôle.

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
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statique) Informe l’évier du conteneur qu’une propriété de contrôle a changé.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statique) Informe l’évier du conteneur qu’une propriété de contrôle est sur le point de changer.|

## <a name="remarks"></a>Notes

`CFirePropNotifyEvent`a deux méthodes qui avertissent l’évier du conteneur qu’une propriété de contrôle a changé ou est sur le point de changer.

Si la mise en œuvre `CFirePropNotifyEvent` de votre contrôle par `FireOnRequestEdit` `FireOnChanged`classe est dérivée, `IPropertyNotifySink`les méthodes sont invoquées lorsque vous appelez ou . Si votre classe de `IPropertyNotifySink`contrôle n’est pas dérivée , les appels à ces fonctions retournent S_OK.

Pour plus d’informations sur la création de contrôles, voir le [tutoriel ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Informe toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété de l’objet spécifié a changé.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Pointeur `IUnknown` vers l’objet envoyant la notification.

*dispID*<br/>
[dans] Identification de la propriété qui a changé.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est sûre à appeler même si votre contrôle ne prend pas en charge les points de connexion.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Informe toutes les interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) connectées (sur chaque point de connexion de l’objet) que la propriété de l’objet spécifié est sur le point de changer.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Pointeur `IUnknown` vers l’objet envoyant la notification.

*dispID*<br/>
[dans] Identifiant de la propriété sur le point de changer.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est sûre à appeler même si votre contrôle ne prend pas en charge les points de connexion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
