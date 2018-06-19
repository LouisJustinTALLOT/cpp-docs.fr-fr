---
title: masqué | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 444994f046b58fbd54dcd3982836bb7fc4d53ed1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879683"
---
# <a name="hidden"></a>hidden
Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[hidden]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **masqué** attribut C++ a les mêmes fonctionnalités que le [masqué](http://msdn.microsoft.com/library/windows/desktop/aa366861) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [pouvant être liés](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **masqué**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`, **classe**, `struct`, méthode, propriété|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclasse** (quand il s’applique à une **classe** ou un `struct`)|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
