---
title: inclut (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::includes
dev_langs:
- C++
helpviewer_keywords:
- includes function [STL/CLR]
ms.assetid: 566307f4-92e0-4acc-ba49-caa48f3ec744
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 34b14f34dd83c405bfcd870314c318587df61134
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128077"
---
# <a name="includes-stlclr"></a>includes (STL/CLR)
Teste si une plage triée contient tous les éléments d’une autre plage triée. Le critère de tri ou d’équivalence entre les éléments peut être spécifié par un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `includes`. Pour plus d’informations, consultez [inclut](../standard-library/algorithm-functions.md#includes).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)