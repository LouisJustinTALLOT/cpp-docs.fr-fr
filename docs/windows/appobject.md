---
title: appobject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.appobject
dev_langs:
- C++
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78cc02c4f4d39b2bcba4c79a07ec84b9657cb66b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651195"
---
# <a name="appobject"></a>appobject
Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans ce [bibliothèque de types](../mfc/automation-clients-using-type-libraries.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[appobject]  
```  
  
## <a name="remarks"></a>Notes  
 Le **appobject** attribut C++ a les mêmes fonctionnalités que le [appobject](http://msdn.microsoft.com/library/windows/desktop/aa366726) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre une simple définition de classe précédée d’un bloc d’attributs qui inclut **appobject**:  
  
```cpp  
// cpp_attr_ref_appobject.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];  
  
[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]  
__interface ICustom {};  
  
[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]  
class A : public ICustom {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|`coclass`|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   