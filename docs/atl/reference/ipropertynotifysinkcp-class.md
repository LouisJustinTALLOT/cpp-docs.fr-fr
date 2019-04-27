---
title: IPropertyNotifySinkCP Class
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: b96e5345923d04de74dace173a80b8c4d3ee917f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197888"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP Class

Cette classe expose [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interface comme une interface sortante sur un objet connectable.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPropertyNotifySinkCP`.

*CDV*<br/>
Une classe qui gère les connexions entre un point de connexion et ses récepteurs. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet un nombre illimité de connexions. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.

## <a name="remarks"></a>Notes

`IPropertyNotifySinkCP` hérite de toutes les méthodes via sa classe de base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

Le [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interface permet à un objet de récepteur recevoir des notifications sur les modifications de propriété. Classe `IPropertyNotifySinkCP` expose cette interface comme une interface sortante sur un objet connectable. Le client doit implémenter le `IPropertyNotifySink` méthodes sur le récepteur.

Dérivez votre classe de `IPropertyNotifySinkCP` lorsque vous souhaitez créer un point de connexion qui représente le `IPropertyNotifySink` interface.

Pour plus d’informations sur l’utilisation de points de connexion dans ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

## <a name="see-also"></a>Voir aussi

[IConnectionPointImpl, classe](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl, classe](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
