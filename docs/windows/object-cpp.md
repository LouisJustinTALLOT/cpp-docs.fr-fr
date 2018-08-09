---
title: objet (C++) | Microsoft Docs
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
ms.openlocfilehash: 2667c8ecb14e31388737366c4de6c527bdc40f9d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012750"
---
# <a name="object-c"></a>object (C++)
Identifie une interface personnalisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[object]  
```  
  
## <a name="remarks"></a>Notes  
 Lorsqu’il précède une définition d’interface, le **objet** attribut C++ provoque l’interface à placer dans le fichier .idl comme une interface personnalisée.  
  
 N’importe quelle interface marquée avec l’objet doit hériter `IUnknown`. Cette condition est remplie si une des interfaces de base héritent `IUnknown`. Si aucune interface de base ne hérite `IUnknown`, le compilateur entraîne l’interface marquée avec **objet** de dériver de `IUnknown`.  
  
## <a name="example"></a>Exemple  
 Consultez [nonbrowsable](../windows/nonbrowsable.md) pour obtenir un exemple montrant comment utiliser **objet**.  
  
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
 [Double](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Personnalisé](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   