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
ms.openlocfilehash: 93ced38ca30a2fd4a61bb3a3664967416fcaf599
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603486"
---
# <a name="include-c"></a>include (C++)
Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Le code suivant montre un exemple montrant comment utiliser **incluent**. Pour cet exemple, le fichier include.h contient uniquement un #include instruction.  
  
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