---
title: partial_sum (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c8141e93d7c8101c9bbfaea08c317748cd44f87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159156"
---
# <a name="partialsum-stlclr"></a>partial_sum (STL/CLR)
Calcule une série de sommes dans une plage d’entrée du premier élément via le `i`élément th et stocke le résultat de chaque somme dans `i`ième élément d’une plage de destination ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacé par une autre opération binaire spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de bibliothèque Standard C++ numérique `partial_sum`. Pour plus d’informations, consultez [partial_sum](../standard-library/numeric-functions.md#partial_sum).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/numeric >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)