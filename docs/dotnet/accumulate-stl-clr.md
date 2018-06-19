---
title: accumuler (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::accumulate
dev_langs:
- C++
helpviewer_keywords:
- accumulate function [STL/CLR]
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 128fe8e46c24b8e0595fe19c0075933d3e5069a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103162"
---
# <a name="accumulate-stlclr"></a>accumulate (STL/CLR)
Calcule la somme de tous les éléments d’une plage spécifiée incluant une valeur initiale en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de bibliothèque Standard C++ numérique `accumulate`. Pour plus d’informations, consultez [s’accumulent](../standard-library/numeric-functions.md#accumulate).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/numeric >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)