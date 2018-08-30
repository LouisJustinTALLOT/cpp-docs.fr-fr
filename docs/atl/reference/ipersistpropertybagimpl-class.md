---
title: Ipersistpropertybagimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b0acfc1fc1f9147a6acbe8bbfe66016dc0b54b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201700"
---
# <a name="ipersistpropertybagimpl-class"></a>Ipersistpropertybagimpl, classe
Cette classe implémente `IUnknown` et permet à un objet enregistrer ses propriétés dans un sac de propriétés fourni par le client.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Initialise un objet nouvellement créé. L’implémentation de ATL retourne S_OK.|  
|[IPersistPropertyBagImpl::Load](#load)|Charge les propriétés de l’objet à partir d’un jeu de propriétés fourni par le client.|  
|[IPersistPropertyBagImpl::Save](#save)|Enregistre les propriétés de l’objet dans un conteneur de propriétés fourni par le client.|  
  
## <a name="remarks"></a>Notes  
 Le [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) interface permet à un objet enregistrer ses propriétés dans un sac de propriétés fourni par le client. Classe `IPersistPropertyBagImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.  
  
 `IPersistPropertyBag` fonctionne en association avec [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) et [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Ces deux interfaces ce dernier doivent être implémentées par le client. Via `IPropertyBag`, le client enregistre et charge les propriétés individuelles de l’objet. Via `IErrorLog`, l’objet et le client peuvent signaler toutes les erreurs rencontrées.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID  
 Récupère le CLSID de l’objet.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) dans le Kit de développement logiciel Windows.  
  
##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew  
 Initialise un objet nouvellement créé.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) dans le Kit de développement logiciel Windows.  
  
##  <a name="load"></a>  IPersistPropertyBagImpl::Load  
 Charge les propriétés de l’objet à partir d’un jeu de propriétés fourni par le client.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Notes  
 ATL utilise le mappage des propriétés de l’objet à récupérer ces informations.  
  
 Consultez [IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) dans le Kit de développement logiciel Windows.  
  
##  <a name="save"></a>  IPersistPropertyBagImpl::Save  
 Enregistre les propriétés de l’objet dans un conteneur de propriétés fourni par le client.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Notes  
 ATL utilise le mappage des propriétés de l’objet pour stocker ces informations. Par défaut, cette méthode enregistre toutes les propriétés, quelle que soit la valeur de *fSaveAllProperties*.  
  
 Consultez [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
