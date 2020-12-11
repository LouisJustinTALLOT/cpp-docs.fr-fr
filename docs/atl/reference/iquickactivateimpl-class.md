---
description: 'En savoir plus sur : classe IQuickActivateImpl'
title: IQuickActivateImpl, classe
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
ms.openlocfilehash: 1e9dc2891351512ec3ebe54ebe6711ee9d4a3fa0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158125"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl, classe

Cette classe combine l’initialisation des contrôles des conteneurs en un seul appel.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IQuickActivateImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Récupère la taille d’affichage actuelle d’un contrôle en cours d’exécution.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Effectue l’initialisation rapide des contrôles en cours de chargement.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informe le contrôle de l’espace d’affichage que le conteneur a affecté.|

## <a name="remarks"></a>Notes

L’interface [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) aide les conteneurs à éviter des retards lors du chargement des contrôles en combinant l’initialisation dans un appel unique. La `QuickActivate` méthode permet au conteneur de passer un pointeur vers une structure [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) qui contient des pointeurs vers toutes les interfaces dont le contrôle a besoin. Au retour, le contrôle retourne un pointeur vers une structure [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) qui contient des pointeurs vers ses propres interfaces, qui sont utilisées par le conteneur. `IQuickActivateImpl`La classe fournit une implémentation par défaut de `IQuickActivate` et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a> IQuickActivateImpl::GetContentExtent

Récupère la taille d’affichage actuelle d’un contrôle en cours d’exécution.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est pour un rendu complet du contrôle et est spécifiée en unités HIMETRIC.

Consultez [IQuickActivate :: GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) dans le SDK Windows.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a> IQuickActivateImpl::QuickActivate

Effectue l’initialisation rapide des contrôles en cours de chargement.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Notes

La structure contient des pointeurs vers les interfaces requises par le contrôle et les valeurs de certaines propriétés ambiantes. Lors du retour, le contrôle passe un pointeur vers une structure [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) qui contient des pointeurs vers ses propres interfaces requises par le conteneur, ainsi que des informations d’État supplémentaires.

Consultez [IQuickActivate :: QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) dans le SDK Windows.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a> IQuickActivateImpl::SetContentExtent

Informe le contrôle de l’espace d’affichage que le conteneur a affecté.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est spécifiée en unités HIMETRIC.

Consultez [IQuickActivate :: SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
