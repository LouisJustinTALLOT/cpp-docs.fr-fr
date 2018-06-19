---
title: nombre (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::count
dev_langs:
- C++
helpviewer_keywords:
- count function [STL/CLR]
ms.assetid: 6d10abb4-3c48-469c-804c-281015b12865
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4992874a6bede4e62dc7035ea755a83681a907eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105008"
---
# <a name="count-stlclr"></a>count (STL/CLR)
Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _Ty> inline  
    typename iterator_traits<_InIt>::difference_type  
        count(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `count`. Pour plus d’informations, consultez [nombre](../standard-library/algorithm-functions.md#count).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)