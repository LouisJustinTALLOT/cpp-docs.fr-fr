---
title: ID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a89758933aef4646aaf11d08d7193d48a44f468
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013543"
---
# <a name="id"></a>ID
Spécifie un *dispid* paramètre pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ id(  
   dispid  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 L’ID de dispatch pour la méthode d’interface.  
  
## <a name="remarks"></a>Notes  
 Le **id** attribut C++ a les mêmes fonctionnalités que le [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [peut être liée](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **id**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [Attributs de membre de données](../windows/data-member-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [in](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   