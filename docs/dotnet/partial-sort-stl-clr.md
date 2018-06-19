---
title: partial_sort (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partial_sort
dev_langs:
- C++
helpviewer_keywords:
- partial_sort function [STL/CLR]
ms.assetid: 5a73b275-aef0-4bda-8ae3-7c1196fe49c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fad07bb56e4e6a6fa85a6fb25b98c114df72e4bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159975"
---
# <a name="partialsort-stlclr"></a>partial_sort (STL/CLR)
Réorganise un nombre spécifié d’éléments plus petits au sein d’une plage, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _RanIt> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `partial_sort`. Pour plus d’informations, consultez [partial_sort](../standard-library/algorithm-functions.md#partial_sort).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)