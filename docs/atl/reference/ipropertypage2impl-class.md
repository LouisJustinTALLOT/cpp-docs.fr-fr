---
title: Classe de IPropertyPage2Impl
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
ms.openlocfilehash: bf76182242f7b76e3a2c18f85b72674e88afa737
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287503"
---
# <a name="ipropertypage2impl-class"></a>Classe de IPropertyPage2Impl

Cette classe implémente `IUnknown` et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPropertyPage2Impl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Spécifie quel contrôle de la propriété reçoit le focus lorsque la page de propriétés est activée. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Le [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interface étend [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) en ajoutant le `EditProperty` (méthode). Cette méthode permet à un client sélectionner une propriété spécifique dans un objet de page de propriétés.

Classe `IPropertyPage2Impl` renvoie simplement E_NOTIMPL pour `IPropertyPage2::EditProperty`. Toutefois, il hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

Lorsque vous créez une page de propriétés, votre classe est généralement dérivée `IPropertyPageImpl`. Pour fournir la prise en charge supplémentaire de `IPropertyPage2`, modifiez votre définition de classe et substituer les `EditProperty` (méthode).

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl.h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Spécifie quel contrôle de la propriété reçoit le focus lorsque la page de propriétés est activée.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPropertyPage2::EditProperty](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage2-editproperty) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[IPerPropertyBrowsingImpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
