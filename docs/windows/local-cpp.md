---
title: local (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17a57ad56402b345aa64e4e4fd02bc57dd7f0321
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877915"
---
# <a name="local-c"></a>local (C++)
Lorsqu’il est utilisé dans l’en-tête de l’interface, vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le `local` attribut C++ a les mêmes fonctionnalités que le [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez [call_as](../windows/call-as.md) pour obtenir un exemple montrant comment utiliser `local`.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`, méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|**dispinterface**|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
