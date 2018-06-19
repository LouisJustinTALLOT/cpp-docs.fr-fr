---
title: v1_enum | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.v1_enum
dev_langs:
- C++
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3156554f5d2b799a9e1ef5a067d1f2e8e600d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890659"
---
# <a name="v1enum"></a>v1_enum
Indique que le type énuméré spécifié être transmis en tant qu’une entité de 32 bits au lieu de la valeur par défaut de 16 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[v1_enum]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **v1_enum** attribut C++ a les mêmes fonctionnalités que le [v1_enum](http://msdn.microsoft.com/library/windows/desktop/aa367303) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre une utilisation de **v1_enum**:  
  
```  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Type énuméré|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
