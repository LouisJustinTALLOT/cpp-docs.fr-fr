---
title: propputref | Documents Microsoft
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
ms.openlocfilehash: 3ac9784e450746a4474879aae346a4242bbe2fd2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878188"
---
# <a name="propputref"></a>propputref
Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[propputref]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **propputref** attribut C++ a les mêmes fonctionnalités que le [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [pouvant être liés](../windows/bindable.md) pour un exemple d’utilisation de **propputref**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|**propget**, **propput**|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   
