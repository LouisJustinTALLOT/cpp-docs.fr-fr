---
title: switch_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f79aa2683948d54f900c92304cdff29647819a74
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650594"
---
# <a name="switchtype"></a>switch_type
Identifie le type de la variable utilisée en tant que l’union discriminante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[switch_type(  
type  
}]  
```  
  
### <a name="parameters"></a>Paramètres  
 *type*  
 Le type de commutateur, peut être un type entier, caractère, booléen ou d’énumération.  
  
## <a name="remarks"></a>Notes  
 Le **switch_type** attribut C++ a les mêmes fonctionnalités que le [switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) attribut MIDL.  
  
 Attributs C++ ne gèrent pas [encapsulé unions](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Unions nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) sont pris en charge uniquement sous la forme suivante :  
  
```cpp  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>Exemple  
 Consultez le [cas](../windows/case-cpp.md) exemple pour un exemple d’utilisation de **switch_type**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**typedef**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   