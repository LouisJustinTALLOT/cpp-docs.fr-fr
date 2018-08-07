---
title: last_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0519409e71457ca025318a591772faf33592abe
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606066"
---
# <a name="lastis"></a>last_is
Spécifie l’index du dernier élément de tableau doit être transmis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ last_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *Expression*  
 Une ou plusieurs expressions de langage C. Emplacements d’arguments vide sont autorisés.  
  
## <a name="remarks"></a>Notes  
 Le **last_is** attribut C++ a les mêmes fonctionnalités que le [last_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   