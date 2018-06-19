---
title: call_as | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68707ea7e00665d12165c7838b1a2ad3440f944d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860864"
---
# <a name="callas"></a>call_as
Permet à un [local](../windows/local-cpp.md) fonction d’être mappée à une fonction distante afin que lorsque la fonction à distance est appelée, la fonction locale est appelée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *function*  
 La fonction locale que vous souhaitez être appelé lorsqu’une fonction distante est appelée.  
  
## <a name="remarks"></a>Notes  
 Le **call_as** attribut C++ a les mêmes fonctionnalités que le [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment vous pouvez utiliser **call_as** pour mapper une fonction non accessibles à distance (**f1**) à une fonction accessible à distance (**Remf1**) :  
  
```  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [Local](../windows/local-cpp.md)   
