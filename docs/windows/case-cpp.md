---
title: cas (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30d665861688054a4f6b7491f449014afe646c71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860955"
---
# <a name="case-c"></a>cas (C++)
Utilisé avec le [switch_type](../windows/switch-type.md) d’attribut dans un **union**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *valeur*  
 Une valeur d’entrée possible pour lequel vous souhaitez fournir le traitement. Le type de **valeur** peut être un des types suivants :  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 ou un identificateur d’un tel type.  
  
## <a name="remarks"></a>Notes  
 Le **cas** attribut C++ a les mêmes fonctionnalités que le **cas** attribut MIDL. Cet attribut est utilisé uniquement avec les [switch_type](../windows/switch-type.md) attribut.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre une utilisation de la **cas** attribut :  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Membre d’un **classe** ou `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
