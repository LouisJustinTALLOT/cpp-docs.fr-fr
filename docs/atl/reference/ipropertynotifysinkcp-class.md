---
title: Classe IPropertyNotifySinkCP
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329607"
---
# <a name="ipropertynotifysinkcp-class"></a>Classe IPropertyNotifySinkCP

Cette classe expose [l’interface IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) comme une interface sortante sur un objet connectable.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPropertyNotifySinkCP`dérivée de .

*Cdv*<br/>
Une classe qui gère les connexions entre un point de connexion et ses éviers. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), qui permet des connexions illimitées. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.

## <a name="remarks"></a>Notes

`IPropertyNotifySinkCP`hérite de toutes les méthodes à travers sa classe de base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

[L’interface IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) permet à un objet d’évier de recevoir des notifications sur les changements de propriété. Class `IPropertyNotifySinkCP` expose cette interface comme une interface sortante sur un objet connectable. Le client doit `IPropertyNotifySink` mettre en œuvre les méthodes sur l’évier.

Dérivez votre `IPropertyNotifySinkCP` classe à partir de quand `IPropertyNotifySink` vous voulez créer un point de connexion qui représente l’interface.

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="see-also"></a>Voir aussi

[Classe IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Classe IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
