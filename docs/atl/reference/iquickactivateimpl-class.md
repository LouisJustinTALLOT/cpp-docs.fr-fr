---
title: Classe IQuickActivateImpl
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
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329553"
---
# <a name="iquickactivateimpl-class"></a>Classe IQuickActivateImpl

Cette classe combine l’initialisation de contrôle des conteneurs en un seul appel.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IQuickActivateImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Récupère la taille actuelle de l’écran pour un contrôle en cours d’exécution.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Effectue une initialisation rapide des commandes chargées.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informe le contrôle de l’espace d’affichage que le conteneur lui a assigné.|

## <a name="remarks"></a>Notes

[L’interface IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) permet aux conteneurs d’éviter les retards lors des contrôles de chargement en combinant la initialisation en un seul appel. La `QuickActivate` méthode permet au conteneur de passer un pointeur à une structure [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) qui détient des indications à toutes les interfaces dont les besoins de contrôle. Au retour, le contrôle passe en arrière un pointeur à une structure [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) qui détient des indications à ses propres interfaces, qui sont utilisés par le conteneur. La `IQuickActivateImpl` classe fournit `IQuickActivate` une mise `IUnknown` en œuvre par défaut et des implémentations en envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Récupère la taille actuelle de l’écran pour un contrôle en cours d’exécution.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est pour un rendu complet du contrôle et est spécifiée dans les unités HIMETRIC.

Voir [IQuickActivate::GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) dans le Windows SDK.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Effectue une initialisation rapide des commandes chargées.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Notes

La structure contient des indications sur les interfaces nécessaires au contrôle et aux valeurs de certaines propriétés ambiantes. Au retour, le contrôle passe un pointeur à une structure [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) qui contient des indications sur ses propres interfaces que le conteneur nécessite, et des informations supplémentaires sur l’état.

Voir [IQuickActivate:QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) in the Windows SDK.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informe le contrôle de l’espace d’affichage que le conteneur lui a assigné.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Notes

La taille est spécifiée dans les unités HIMETRIC.

Voir [IQuickActivate::SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
