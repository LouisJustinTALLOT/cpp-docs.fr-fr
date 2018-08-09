---
title: size_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dbb3bfbf61c4ad7303c6cee272e14fc91bc9656
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011853"
---
# <a name="sizeis"></a>size_is
Spécifiez la taille de mémoire allouée pour les pointeurs de taille, en taille réelle des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ size_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *Expression*  
 La taille de mémoire allouée pour les pointeurs de taille.  
  
## <a name="remarks"></a>Notes  
 Le **size_is** attribut C++ a les mêmes fonctionnalités que le [size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|`max_is`|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de paramètre](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   