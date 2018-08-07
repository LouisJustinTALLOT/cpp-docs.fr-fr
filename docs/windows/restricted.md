---
title: restreint | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f79b4e53947e0e87fb70211ca40bc54f4500855f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602770"
---
# <a name="restricted"></a>restricted
Spécifie qu’un membre d’un module, une interface ou une dispinterface ne peut pas être appelé arbitrairement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ restricted(  
   interfaces  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *interfaces*  
 Une ou plusieurs interfaces qui ne peuvent pas être appelées arbitrairement sur un objet COM. Ce paramètre est uniquement valide lorsqu’il est appliqué à une classe.  
  
## <a name="remarks"></a>Notes  
 Le **restreint** attribut C++ a les mêmes fonctionnalités que le [restreint](http://msdn.microsoft.com/library/windows/desktop/aa367157) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **restreint** attribut :  
  
```cpp  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode, d’interface **interface**, **classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclasse** (lorsqu’il est appliqué à **classe** ou **struct**)|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   