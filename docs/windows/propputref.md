---
title: propputref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72fa9523b850e5c7d76b587c37b181f21df25c0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013978"
---
# <a name="propputref"></a>propputref
Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[propputref]  
```  
  
## <a name="remarks"></a>Notes  
 Le **propputref** attribut C++ a les mêmes fonctionnalités que le [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **propputref**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|`propget`, `propput`|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   