---
title: prev_permutation (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::prev_permutation
dev_langs:
- C++
helpviewer_keywords:
- prev_permutation function [STL/CLR]
ms.assetid: 5294dbe5-1b5f-4369-a764-067dff86d1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7ae545d56f6c9433e294a59f0af580e974e32ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159377"
---
# <a name="prevpermutation-stlclr"></a>prev_permutation (STL/CLR)
Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `prev_permutation`. Pour plus d’informations, consultez [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)