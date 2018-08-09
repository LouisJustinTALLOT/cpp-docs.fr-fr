---
title: dans (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8522b3af527267706a2e2697b88049a38b0f092f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017189"
---
# <a name="in-c"></a>in (C++)
Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[in]  
```  
  
## <a name="remarks"></a>Notes  
 Le **dans** attribut C++ a les mêmes fonctionnalités que le [dans](http://msdn.microsoft.com/library/windows/desktop/aa367051) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez [peut être liée](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **dans**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Paramètre d’interface, méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|**retval**|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [ID](../windows/id.md)   
 [out](../windows/out-cpp.md)   