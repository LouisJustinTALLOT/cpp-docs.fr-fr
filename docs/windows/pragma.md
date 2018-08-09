---
title: pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9c9d347b319afc3ee84818e74029a98b1aa5484
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014297"
---
# <a name="pragma"></a>pragma
Émet la chaîne spécifiée dans le fichier .idl généré sans utiliser de guillemets. 
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ pragma(  
   pragma_statement  
) ];  
```  
  
### <a name="parameters"></a>Paramètres  
 *pragma_statement*  
 Le pragma que vous souhaitez aller dans le fichier .idl généré.  
  
## <a name="remarks"></a>Notes  
 Le **pragma** attribut C++ a les mêmes fonctionnalités que le [pragma](http://msdn.microsoft.com/library/windows/desktop/aa367143) attribut MIDL.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cpp_attr_ref_pragma.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[pragma(pack(4))];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A  
{  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [pack](../preprocessor/pack.md)   