---
title: IPropertyPage2Impl, classe
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
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495609"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl, classe

Cette classe implémente `IUnknown` et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IPropertyPage2Impl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Spécifie le contrôle de propriété qui recevra le focus lorsque la page de propriétés sera activée. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

L’interface [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) étend [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) en ajoutant la `EditProperty` méthode. Cette méthode permet à un client de sélectionner une propriété spécifique dans un objet de page de propriétés.

La `IPropertyPage2Impl` classe retourne simplement E_NOTIMPL `IPropertyPage2::EditProperty`pour. Toutefois, il hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

Lorsque vous créez une page de propriétés, votre classe est généralement dérivée de `IPropertyPageImpl`. Pour fournir la prise en charge `IPropertyPage2`supplémentaire de, modifiez votre définition de classe et `EditProperty` substituez la méthode.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Spécifie le contrôle de propriété qui recevra le focus lorsque la page de propriétés sera activée.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IPerPropertyBrowsingImpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
