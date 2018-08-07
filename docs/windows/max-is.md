---
title: max_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fae7ee95255d72d2799a5913821606f770e2b3b
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608428"
---
# <a name="maxis"></a>max_is
Désigne la valeur maximale pour un index de tableau valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ max_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression*  
 Une ou plusieurs expressions de langage C. Emplacements d’arguments vide sont autorisés.  
  
## <a name="remarks"></a>Notes  
 Le **max_is** attribut C++ a les mêmes fonctionnalités que le [max_is](http://msdn.microsoft.com/library/windows/desktop/aa367074) attribut MIDL.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|**size_is**|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Exemple  
 Consultez [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   