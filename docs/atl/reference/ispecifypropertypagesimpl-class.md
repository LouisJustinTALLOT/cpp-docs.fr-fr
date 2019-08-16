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
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495413"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `ISpecifyPropertyPagesImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Remplit un tableau compté de valeurs UUID. Chaque UUID correspond au CLSID de l’une des pages de propriétés qui peuvent être affichées dans la feuille de propriétés de l’objet.|

## <a name="remarks"></a>Notes

L’interface [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) permet à un client d’obtenir une liste de CLSID pour les pages de propriétés prises en charge par un objet. La `ISpecifyPropertyPagesImpl` classe fournit une implémentation par défaut de cette interface et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

> [!NOTE]
>  N’exposez `ISpecifyPropertyPages` pas l’interface si votre objet ne prend pas en charge les pages de propriétés.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Remplit le tableau dans la structure [cauuid](/windows/win32/api/ocidl/ns-ocidl-cauuid) avec les CLSID des pages de propriétés qui peuvent être affichées dans la feuille de propriétés de l’objet.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour récupérer chaque CLSID.

Consultez [ISpecifyPropertyPages:: GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IPropertyPageImpl, classe](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
