---
description: 'En savoir plus sur : classe IPropertyPage2Impl'
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
ms.openlocfilehash: 8311746b03c4c680a040c0873ee58f936044dd9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139280"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl, classe

Cette classe implémente `IUnknown` et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPropertyPage2Impl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Spécifie le contrôle de propriété qui recevra le focus lorsque la page de propriétés sera activée. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

L’interface [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) étend [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) en ajoutant la `EditProperty` méthode. Cette méthode permet à un client de sélectionner une propriété spécifique dans un objet de page de propriétés.

La classe `IPropertyPage2Impl` retourne simplement E_NOTIMPL pour `IPropertyPage2::EditProperty` . Toutefois, il hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

Lorsque vous créez une page de propriétés, votre classe est généralement dérivée de `IPropertyPageImpl` . Pour fournir la prise en charge supplémentaire de `IPropertyPage2` , modifiez votre définition de classe et substituez la `EditProperty` méthode.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a> IPropertyPage2Impl::EditProperty

Spécifie le contrôle de propriété qui recevra le focus lorsque la page de propriétés sera activée.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPropertyPage2 :: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IPerPropertyBrowsingImpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
