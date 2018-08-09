---
title: local (C++) | Microsoft Docs
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
ms.openlocfilehash: ad1fb4dd281918b0d9ab3494c9a9f060468fc389
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018095"
---
# <a name="local-c"></a>local (C++)
Lorsqu’il est utilisé dans l’en-tête de l’interface, vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[local]  
```  
  
## <a name="remarks"></a>Notes  
 Le **local** attribut C++ a les mêmes fonctionnalités que le [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez [call_as](../windows/call-as.md) pour obtenir un exemple montrant comment utiliser **local**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**interface**, méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|`dispinterface`|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   