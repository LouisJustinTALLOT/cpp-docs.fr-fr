---
title: partition (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partition
dev_langs:
- C++
helpviewer_keywords:
- partition function [STL/CLR]
ms.assetid: 3f551eb3-31ec-4b1d-b585-07718d6a1bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 91da41eee64ca5f818cb8dfcbc9a7517f3aed144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159234"
---
# <a name="partition-stlclr"></a>partition (STL/CLR)
Répartit les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `partition`. Pour plus d’informations, consultez [partition](../standard-library/algorithm-functions.md#partition).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)