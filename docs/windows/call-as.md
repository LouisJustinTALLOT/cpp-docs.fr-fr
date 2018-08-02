---
title: call_as | Microsoft Docs
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
ms.openlocfilehash: 8fb431c6aad10f7e974ed139ddf83cfb0a58d30a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465868"
---
# <a name="callas"></a>call_as
Permet une [local](../windows/local-cpp.md) fonction être mappée à une fonction à distance afin que lorsque la fonction à distance est appelée, la fonction locale soit appelée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *function*  
 La fonction locale que vous souhaitez être appelée lorsqu’une fonction à distance est appelée.  
  
## <a name="remarks"></a>Notes  
 Le **call_as** attribut C++ a les mêmes fonctionnalités que le [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment vous pouvez utiliser **call_as** pour mapper une fonction non accessibles à distance (**f1**) à une fonction accessible à distance (**Remf1**) :  
  
```cpp  
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
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [local](../windows/local-cpp.md)   