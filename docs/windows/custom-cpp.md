---
title: personnalisé (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b37d87d5380b9d4dac69cee702654285461ead6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871625"
---
# <a name="custom-c"></a>custom (C++)
Définit les métadonnées pour un objet dans la bibliothèque de types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>Paramètres  
 *uuid*  
 ID unique.  
  
 *valeur*  
 Une valeur qui peut être placée dans un variant.  
  
## <a name="remarks"></a>Notes  
 Le **personnalisé** attribut C++ entraîne à placer dans la bibliothèque de types d’informations. Vous devez un outil qui lit la valeur personnalisée à partir de la bibliothèque de types.  
  
 Le **personnalisé** attribut a les mêmes fonctionnalités que le [personnalisé](http://msdn.microsoft.com/library/windows/desktop/aa366766) attribut MIDL.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Non-COM `interface`, **classe**, `enum`s, `idl_module` méthodes, les membres d’interface, les paramètres de l’interface, `typedef`s, **union**s, `struct`s|  
|**Renouvelable**|Oui|  
|**Attributs requis**|**coclasse** (lorsqu’il est utilisé pour la classe)|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
