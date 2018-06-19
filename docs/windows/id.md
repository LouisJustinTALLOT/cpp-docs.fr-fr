---
title: ID | Documents Microsoft
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
ms.openlocfilehash: 6c674765a0dfc06648d64a2b3b4e820bb467e700
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882445"
---
# <a name="id"></a>ID
Spécifie un `dispid` paramètre pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 L’ID de dispatch de la méthode d’interface.  
  
## <a name="remarks"></a>Notes  
 Le **id** attribut C++ a les mêmes fonctionnalités que le [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [pouvant être liés](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **id**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [Attributs de membre de données](../windows/data-member-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [in](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   
