---
title: Classe IPropertyPage2Impl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329594"
---
# <a name="ipropertypage2impl-class"></a>Classe IPropertyPage2Impl

Cette classe `IUnknown` implémente et hérite de la mise en œuvre par défaut [d’IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPropertyPage2Impl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Précise quel contrôle de propriété recevra l’accent lorsque la page de propriété sera activée. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

[L’interface IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) étend [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) en ajoutant la `EditProperty` méthode. Cette méthode permet à un client de sélectionner une propriété spécifique dans un objet de page de propriété.

Classe `IPropertyPage2Impl` retourne simplement E_NOTIMPL `IPropertyPage2::EditProperty`pour . Cependant, il hérite de la mise en œuvre par défaut [d’IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

Lorsque vous créez une page de propriété, votre classe est généralement dérivée de `IPropertyPageImpl`. Pour fournir le `IPropertyPage2`soutien supplémentaire de , modifier `EditProperty` la définition de votre classe et remplacer la méthode.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertyPage2Impl::EditProperty

Précise quel contrôle de propriété recevra l’accent lorsque la page de propriété sera activée.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IPropertyPage2:EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Classe IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
