---
title: retval | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4364f60012cb4571edbf195a02b77f500a2dc86
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010329"
---
# <a name="retval"></a>retval
Désigne le paramètre qui reçoit la valeur de retour du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[retval]  
```  
  
## <a name="remarks"></a>Notes  
 Le **retval** attribut C++ a les mêmes fonctionnalités que le [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) attribut MIDL.  
  
 **retval** doit apparaître sur le dernier argument dans les déclaration d’une fonction.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **retval**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Paramètre d’interface, méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|**out**|  
|**Attributs non valides**|**in**|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   