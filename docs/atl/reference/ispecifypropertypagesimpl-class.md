---
title: ISpecifyPropertyPagesImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d784d7f3c03b18d2f81d6eec8bc9e4b76c7ee8da
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216767"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl, classe
Cette classe implémente `IUnknown` et fournit une implémentation par défaut de la [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `ISpecifyPropertyPagesImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Remplit un valeurs compté le tableau d’UUID. Chaque UUID correspond au CLSID de l’un des pages de propriétés qui peuvent être affichées dans la feuille de propriétés de l’objet.|  
  
## <a name="remarks"></a>Notes  
 Le [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interface permet à un client obtenir une liste des CLSID pour les pages de propriétés pris en charge par un objet. Classe `ISpecifyPropertyPagesImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.  
  
> [!NOTE]
>  N’exposez pas le `ISpecifyPropertyPages` si votre objet ne prend pas en charge les pages de propriétés de l’interface.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages  
 Remplit le tableau le [CAUUID](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid) structure avec les CLSID pour les pages de propriétés qui peuvent être affichées dans la feuille de propriétés de l’objet.  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>Notes  
 ATL utilise le mappage des propriétés de l’objet pour récupérer chaque CLSID.  
  
 Consultez [ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyPageImpl, classe](../../atl/reference/ipropertypageimpl-class.md)   
 [Iperpropertybrowsingimpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
