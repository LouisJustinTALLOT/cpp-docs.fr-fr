---
title: ISpecifyPropertyPagesImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326409"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl, classe

Cette classe `IUnknown` implémente et fournit une implémentation par défaut de l’interface [ISpecifyPropertyPages.](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `ISpecifyPropertyPagesImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Remplit un tableau compté de valeurs UUID. Chaque UUID correspond au CLSID pour l’une des pages de propriété qui peuvent être affichées dans la feuille de propriété de l’objet.|

## <a name="remarks"></a>Notes

[L’interface ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) permet à un client d’obtenir une liste de CLSID pour les pages de propriété supportées par un objet. La `ISpecifyPropertyPagesImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

> [!NOTE]
> N’exposez `ISpecifyPropertyPages` pas l’interface si votre objet ne prend pas en charge les pages de propriété.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

Remplit le tableau de la structure [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) avec les CLSID pour les pages de propriété qui peuvent être affichées dans la feuille de propriété de l’objet.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Notes

ATL utilise la carte de propriété de l’objet pour récupérer chaque CLSID.

Voir [ISpecifyPropertyPages:GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Classe IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
