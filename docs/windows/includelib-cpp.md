---
title: includelib (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e10ab341dc4c90a26315ea5e30f03bc71e628b64
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603379"
---
# <a name="includelib-c"></a>includelib (C++)
Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>Paramètres  
 *Name.idl*  
 Le nom du fichier .idl que vous souhaitez inclus dans le fichier .idl généré.  
  
## <a name="remarks"></a>Notes  
 Le **includelib** attribut C++ génère un fichier .idl ou .h être inclus dans le fichier .idl généré, après la `importlib` instruction.  
  
## <a name="example"></a>Exemple  
 Le code suivant est indiqué dans un fichier .cpp :  
  
```cpp  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Oui|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [Importation](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [inclure](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   