---
title: Fonctions globales de mappage COM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 509479a923203acd80eaac1ef90aa64125d208c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359877"
---
# <a name="com-map-global-functions"></a>Fonctions globales de mappage COM
Ces fonctions fournissent la prise en charge pour le mappage COM **IUnknown** implémentations.  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Délègue à la **IUnknown** d’un objet brutes et non agrégée.|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Génère un code efficace pour comparer des interfaces à **IUnknown**.|  

  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `pThis`  
 [in] Un pointeur vers l’objet qui contient le mappage COM des interfaces exposées à `QueryInterface`.  
  
 `pEntries`  
 [in] Un tableau de **_ATL_INTMAP_ENTRY** structures qui accèdent à un mappage des interfaces disponibles.  
  
 `iid`  
 [in] Le GUID de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface spécifié dans `iid`, ou **NULL** si l’interface est introuvable.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 `AtlInternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégée, `AtlInternalQueryInterface` ne délègue pas à inconnu externe. Vous pouvez entrer des interfaces dans la table de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou une de ses variantes.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 Appelez cette fonction, dans le cas particulier du test de **IUnknown**.  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>Paramètres  
 *rguid1*  
 [in] Le GUID à comparer à **IID_IUnknown**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)   
 [Macros de mappage COM](../../atl/reference/com-map-macros.md)
