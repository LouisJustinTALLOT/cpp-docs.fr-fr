---
title: plage (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac5f0e81a7d29d89e32735224afed67f3d9c9101
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877928"
---
# <a name="range-c"></a>range (C++)
Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ range(  
   low,   
   high  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *low*  
 La valeur de la plage inférieure.  
  
 *high*  
 La valeur de la plage supérieure.  
  
## <a name="remarks"></a>Notes  
 Le **plage** attribut C++ a les mêmes fonctionnalités que le [plage](http://msdn.microsoft.com/library/windows/desktop/aa367151) attribut MIDL.  
  
## <a name="example"></a>Exemple  
  
```  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode d’interface, paramètre d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [Attributs de membre de données](../windows/data-member-attributes.md)   
