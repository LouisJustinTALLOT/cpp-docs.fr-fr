---
title: inclure (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21bb7cf58c3c397237768942d60f79958f3278a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013559"
---
# <a name="include-c"></a>include (C++)
Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ include(  
   header_file  
) ];  
```  
  
### <a name="parameters"></a>Paramètres  
 *HEADER_FILE*  
 Le nom d’un fichier que vous souhaitez inclus dans le fichier .idl généré.  
  
## <a name="remarks"></a>Notes  
 Le **incluent** C++ attribut entraîne une `#include` instruction à être placé sous le `import "docobj.idl"` instruction dans le fichier .idl généré.  
  
 Le **incluent** attribut C++ a les mêmes fonctionnalités que le [incluent](http://msdn.microsoft.com/library/windows/desktop/aa367052) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre un exemple montrant comment utiliser **incluent**. Pour cet exemple, le fichier include.h contient uniquement un `#include` instruction.  
  
```cpp  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [Importation](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   