---
title: make_unsigned, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- make_unsigned
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 1bdebf2a3d3f03defa041d049ac98287df7aad6c
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="makeunsigned-class"></a>make_unsigned, classe
Rend le type ou le plus petit type non signé supérieur ou égal en taille au type.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`T`|Type à modifier.|  
  
## <a name="remarks"></a>Remarques  
 Une instance du modificateur de type contient un type modifié qui est `T` si `is_unsigned<T>` contient la valeur true. Dans le cas contraire, il s'agit du plus petit type signé `ST` pour lequel `sizeof (T) <= sizeof (ST)`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<type_traits>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [<type_traits>](../standard-library/type-traits.md)




