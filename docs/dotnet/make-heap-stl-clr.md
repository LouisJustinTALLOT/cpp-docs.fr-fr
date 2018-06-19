---
title: make_heap (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::make_heap
dev_langs:
- C++
helpviewer_keywords:
- make_heap function [STL/CLR]
ms.assetid: bc1bed28-7a26-4540-901d-5584cd117ea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f1446cba1661e11c18b540bcb60dcb8385e74d76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129874"
---
# <a name="makeheap-stlclr"></a>make_heap (STL/CLR)
Convertit les éléments d’une plage spécifiée en un tas, dans lequel le premier élément est le plus grand, et pour lequel un critère de tri peut être spécifié à l’aide d’un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _RanIt> inline  
    void make_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `make_heap`. Pour plus d’informations, consultez [make_heap](../standard-library/algorithm-functions.md#make_heap).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)