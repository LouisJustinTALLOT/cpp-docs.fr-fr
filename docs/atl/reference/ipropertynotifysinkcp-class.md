---
description: 'En savoir plus sur : classe IPropertyNotifySinkCP'
title: IPropertyNotifySinkCP, classe
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 096a24a22634be23c7ede955c7ae49c3dd963f66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158359"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP, classe

Cette classe expose l’interface [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) comme une interface sortante sur un objet connectable.

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
Votre classe, dérivée de `IPropertyNotifySinkCP` .

*CDV*<br/>
Classe qui gère les connexions entre un point de connexion et ses récepteurs. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet des connexions illimitées. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.

## <a name="remarks"></a>Notes

`IPropertyNotifySinkCP` hérite de toutes les méthodes par le biais de sa classe de base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

L’interface [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) permet à un objet récepteur de recevoir des notifications sur les modifications de propriété. `IPropertyNotifySinkCP`La classe expose cette interface comme une interface sortante sur un objet connectable. Le client doit implémenter les `IPropertyNotifySink` méthodes sur le récepteur.

Dérivez votre classe de `IPropertyNotifySinkCP` lorsque vous souhaitez créer un point de connexion qui représente l' `IPropertyNotifySink` interface.

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="see-also"></a>Voir aussi

[IConnectionPointImpl, classe](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl, classe](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
