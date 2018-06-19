---
title: upper_bound (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- upper_bound function [STL/CLR]
ms.assetid: a377a77b-8005-496e-85ae-b431a9b2f0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be87a8a91f91e3bdb4417f8ec6f0ab0c51a515cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167130"
---
# <a name="upperbound-stlclr"></a>upper_bound (STL/CLR)
Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `upper_bound`. Pour plus d’informations, consultez [upper_bound](../standard-library/algorithm-functions.md#upper_bound).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)