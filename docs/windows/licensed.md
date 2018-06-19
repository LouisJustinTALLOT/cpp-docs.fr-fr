---
title: une licence | Documents Microsoft
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
ms.openlocfilehash: fe7d915d53b246c98372ce8647e35fb996e9a7c4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875745"
---
# <a name="licensed"></a>licensed
Indique que l’objet COM auquel elle s’applique est concédé sous licence et doit être instancié à l’aide de **IClassFactory2**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[licensed]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **concédé sous licence** attribut C++ a les mêmes fonctionnalités que le [concédé sous licence](http://msdn.microsoft.com/library/windows/desktop/aa367070) attribut MIDL.  
  
## <a name="example"></a>Exemple  
  
```  
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
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclass**|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
