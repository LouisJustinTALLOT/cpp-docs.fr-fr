---
title: une licence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.licensed
dev_langs:
- C++
helpviewer_keywords:
- licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a722b7a4eb6104670d2d67d95f1c47755af5938
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012636"
---
# <a name="licensed"></a>licensed
Indique que l’objet COM auquel il s’applique est concédé sous licence et doit être instanciée à l’aide de `IClassFactory2`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[licensed]  
```  
  
## <a name="remarks"></a>Notes  
 Le **concédé sous licence** attribut C++ a les mêmes fonctionnalités que le [concédé sous licence](http://msdn.microsoft.com/library/windows/desktop/aa367070) attribut MIDL.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cpp_attr_ref_licensed.cpp  
// compile with: /LD  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {  
   HRESULT f();  
};  
  
[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),   
licensed, threading(free), progid(some.name)]  
class CSample : public IMyI {  
public:  
   int nSize;  
};  
  
[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|`coclass`|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   