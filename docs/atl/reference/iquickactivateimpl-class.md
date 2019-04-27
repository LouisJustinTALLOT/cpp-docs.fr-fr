---
title: Iquickactivateimpl, classe
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 2a2b11746249b6ee4f6ddd578717aacc374d53bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198146"
---
# <a name="iquickactivateimpl-class"></a>Iquickactivateimpl, classe

Cette classe associe l’initialisation de contrôle de conteneurs dans un seul appel.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IQuickActivateImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Récupère la taille d’affichage actuel pour un contrôle en cours d’exécution.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Effectue une initialisation rapide de contrôles en cours de chargement.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Indique au contrôle de la quantité d’espace affichage le conteneur a attribué à ce dernier.|

## <a name="remarks"></a>Notes

Le [IQuickActivate](/windows/desktop/api/ocidl/nn-ocidl-iquickactivate) interface permet d’éviter les retards lors du chargement des contrôles en combinant l’initialisation dans un seul appel de conteneurs. Le `QuickActivate` méthode permet au conteneur passer un pointeur vers un [QACONTAINER](/windows/desktop/api/ocidl/ns-ocidl-tagqacontainer) structure qui conserve des pointeurs vers toutes les interfaces le contrôle a besoin. En retour, le contrôle passe à nouveau un pointeur vers un [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) structure qui conserve des pointeurs vers ses propres interfaces, qui sont utilisées par le conteneur. Classe `IQuickActivateImpl` fournit une implémentation par défaut de `IQuickActivate` et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent

Récupère la taille d’affichage actuel pour un contrôle en cours d’exécution.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est pour un rendu complet du contrôle et est spécifiée en unités HIMETRIC.

Consultez [IQuickActivate::GetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) dans le Kit de développement logiciel Windows.

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

Effectue une initialisation rapide de contrôles en cours de chargement.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Notes

La structure contient des pointeurs vers les interfaces requises par le contrôle et les valeurs de certaines propriétés ambiantes. Au retour, le contrôle passe un pointeur vers un [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) structure qui contient des pointeurs vers ses propres interfaces nécessitant le conteneur et les informations d’état supplémentaires.

Consultez [IQuickActivate::QuickActivate](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-quickactivate) dans le Kit de développement logiciel Windows.

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

Indique au contrôle de la quantité d’espace affichage le conteneur a attribué à ce dernier.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est spécifiée en unités HIMETRIC.

Consultez [IQuickActivate::SetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
