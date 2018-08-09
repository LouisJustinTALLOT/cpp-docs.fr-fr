---
title: propget | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propget
dev_langs:
- C++
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32170ca02a9d36667ae4d718362774afa0711c60
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019941"
---
# <a name="propget"></a>propget
Spécifie une fonction d’accesseur de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[propget]  
```  
  
## <a name="remarks"></a>Notes  
 Le **propget** attribut C++ a les mêmes fonctionnalités que le [propget](http://msdn.microsoft.com/library/windows/desktop/aa367145) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **propget**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|`propput`, `propputref`|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [propput](../windows/propput.md)   
 [propputref](../windows/propputref.md)   