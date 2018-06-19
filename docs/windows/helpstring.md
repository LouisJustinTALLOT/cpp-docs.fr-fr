---
title: HelpString | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81a3e45c5636fd193b7880e093711b5cc584bf99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879004"
---
# <a name="helpstring"></a>helpstring
Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ helpstring(  
   "string"  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `string`  
 Le texte de la chaîne d’aide.  
  
## <a name="remarks"></a>Notes  
 Le **helpstring** attribut C++ a les mêmes fonctionnalités que le [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [defaultvalue](../windows/defaultvalue.md) pour obtenir un exemple montrant comment utiliser **helpstring**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`, `typedef`, **classe**, méthode, propriété|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpFile](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   
