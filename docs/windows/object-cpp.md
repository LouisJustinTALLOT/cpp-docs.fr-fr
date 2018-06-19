---
title: objet (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 601d67fb48f0ae826474d33e7dca0fbffff9478c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879706"
---
# <a name="object-c"></a>object (C++)
Identifie une interface personnalisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>Notes  
 Lorsqu’il précède une définition d’interface, le **objet** attribut C++ provoque l’interface doit être placé dans le fichier .idl comme une interface personnalisée.  
  
 N’importe quelle interface marquée avec l’objet doit hériter de **IUnknown**. Cette condition est remplie si une des interfaces de base hérite de **IUnknown**. Si aucune interface de base ne hérite de **IUnknown**, le compilateur entraînera l’interface marquée avec **objet** dériver **IUnknown**.  
  
## <a name="example"></a>Exemple  
 Consultez [nonbrowsable](../windows/nonbrowsable.md) pour obtenir un exemple montrant comment utiliser **objet**.  
  
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
 [Double](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Personnalisé](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
