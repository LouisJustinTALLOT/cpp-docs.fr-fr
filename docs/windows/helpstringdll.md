---
title: helpstringdll | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 94e33eea3dc367634b3cae9a025b0189598bbdd1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648949"
---
# <a name="helpstringdll"></a>helpstringdll
Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ helpstringdll(  
   "string"  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *string*  
 La DLL à utiliser pour effectuer la recherche de chaîne de document.  
  
## <a name="remarks"></a>Notes  
 Le **helpstringdll** attribut C++ a les mêmes fonctionnalités que le [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) attribut MIDL.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **interface**, méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   