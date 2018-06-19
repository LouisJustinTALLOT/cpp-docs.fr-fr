---
title: Classe de IPropertyPage2Impl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 204f62e667bd149dd174f960ba31d8388e01394e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361900"
---
# <a name="ipropertypage2impl-class"></a>Classe de IPropertyPage2Impl
Cette classe implémente **IUnknown** et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IPropertyPage2Impl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|Spécifie le contrôle de la propriété reçoit le focus lorsque la page de propriétés est activée. L’implémentation ATL retourne **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Notes  
 Le [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interface étend [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) en ajoutant le `EditProperty` (méthode). Cette méthode permet à un client sélectionner une propriété spécifique dans un objet de page de propriétés.  
  
 Classe `IPropertyPage2Impl` retourne simplement **E_NOTIMPL** pour **IPropertyPage2::EditProperty**. Toutefois, il hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 Lorsque vous créez une page de propriétés, votre classe est généralement dérivée `IPropertyPageImpl`. Pour fournir la prise en charge supplémentaire de **IPropertyPage2**, modifiez votre définition de classe et substituer la `EditProperty` (méthode).  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty  
 Spécifie le contrôle de la propriété reçoit le focus lorsque la page de propriétés est activée.  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Classe de ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
