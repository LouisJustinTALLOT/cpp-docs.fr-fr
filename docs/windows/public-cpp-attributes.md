---
title: public (attributs C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.public
dev_langs:
- C++
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01e8a2874dd756d3f6977730e5463b3089755108
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016650"
---
# <a name="public-c-attributes"></a>public (attributs C++)
Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[public]  
```  
  
## <a name="remarks"></a>Notes  
 Le **public** attribut C++ a les mêmes fonctionnalités que le [public](http://msdn.microsoft.com/library/windows/desktop/aa367150) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **public** attribut :  
  
```cpp  
// cpp_attr_ref_public.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, public] typedef long MEMBERID;  
  
[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(2)] long procedure ([in, optional] VARIANT i);  
};  
```  
  
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
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   