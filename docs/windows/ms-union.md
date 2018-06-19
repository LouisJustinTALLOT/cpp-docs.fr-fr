---
title: ms_union | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ms_union
dev_langs:
- C++
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a377995149fda8efd565c30caff9b7791748ed79
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882035"
---
# <a name="msunion"></a>ms_union
Contrôle l’alignement de représentation sous forme de données de réseau d’unions nonencapsulated.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[ms_union]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **ms_union** attribut C++ a les mêmes fonctionnalités que le [ms_union](http://msdn.microsoft.com/library/windows/desktop/aa367100) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre le positionnement des **ms_union**:  
  
```  
// cpp_attr_ref_ms_union.cpp  
// compile with: /LD  
#include <unknwn.h>  
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl {  
   HRESULT DisplayString([in, string] char * p1);  
};  
  
[export, switch_type(short)] union _WILLIE_UNION_TYPE  {  
   [case(24)]  
      float fMays;  
   [case(25)]  
      double dMcCovey;  
   [default]  
      int x;  
 };  
  
[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Unions nonencapsulated|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|**dispinterface**|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
