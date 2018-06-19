---
title: library_block | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbd97897138edffba12baf47d64465b1f6ca0df4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877889"
---
# <a name="libraryblock"></a>library_block
Place une construction dans le bloc de bibliothèque IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[library_block]  
  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque vous placez une construction dans le bloc de bibliothèque, vous assurez qu’il sera passé dans la bibliothèque de types, indépendamment de si elle est référencée. Par défaut, les seules constructions modifiés par le [coclasse](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), et [idl_module](../windows/idl-module.md) attributs sont placés dans le bloc de bibliothèque.  
  
## <a name="example"></a>Exemple  
 Dans le code suivant, une interface personnalisée est placée dans le bloc de bibliothèque.  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du compilateur](../windows/compiler-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
