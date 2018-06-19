---
title: binary_search (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::binary_search
dev_langs:
- C++
helpviewer_keywords:
- binary_search function [STL/CLR]
ms.assetid: 520869cc-7cd3-4c81-b439-05f042474416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 467efdb6c17dd6f3d9dcf8b7aa8b3495367a92f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105294"
---
# <a name="binarysearch-stlclr"></a>binary_search (STL/CLR)
Teste si un élément d’une plage triée est égal à une valeur spécifiée ou équivalent, selon une condition spécifiée par un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `binary_search`. Pour plus d’informations, consultez [binary_search](../standard-library/algorithm-functions.md#binary_search).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)