---
title: pointer_default | Documents Microsoft
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
ms.openlocfilehash: ee904f9243cf642d3a942d4bc323f5ec381b0480
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877460"
---
# <a name="pointerdefault"></a>pointer_default
Spécifie l’attribut du pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui s’affichent dans les listes de paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ pointer_default(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *valeur*  
 Une valeur qui décrit le type de pointeur : **ptr**, `ref`, ou **unique**.  
  
## <a name="remarks"></a>Notes  
 Le **pointer_default** attribut C++ a les mêmes fonctionnalités que le [pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [defaultvalue](../windows/defaultvalue.md) pour un exemple d’utilisation de **pointer_default**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
