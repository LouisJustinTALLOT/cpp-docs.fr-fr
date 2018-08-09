---
title: pointer_default | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98e3b9e78f46b14dfeca18a8e69538111d3ba219
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010313"
---
# <a name="pointerdefault"></a>pointer_default
Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui s’affichent dans les listes de paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ pointer_default(  
   value  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *valeur*  
 Une valeur qui décrit le type de pointeur : **ptr**, **ref**, ou **unique**.  
  
## <a name="remarks"></a>Notes  
 Le **pointer_default** attribut C++ a les mêmes fonctionnalités que le [pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [defaultvalue](../windows/defaultvalue.md) pour un exemple d’utilisation de **pointer_default**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**interface**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   