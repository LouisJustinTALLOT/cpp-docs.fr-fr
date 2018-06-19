---
title: next_permutation (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::next_permutation
dev_langs:
- C++
helpviewer_keywords:
- next_permutation function [STL/CLR]
ms.assetid: e36e821f-4b8d-461b-8074-69cd0175ccec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36b21ecabb9ab44f1b5c233cffe6567dc8a99eb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133764"
---
# <a name="nextpermutation-stlclr"></a>next_permutation (STL/CLR)
Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `next_permutation`. Pour plus d’informations, consultez [next_permutation](../standard-library/algorithm-functions.md#next_permutation).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)