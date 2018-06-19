---
title: recherche (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::search
dev_langs:
- C++
helpviewer_keywords:
- search function [STL/CLR]
ms.assetid: 3317c7f4-9f47-44b8-a7c7-73948a2f83e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0fb0b045e15c5ab491f0f7a4f2514898526b8fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162744"
---
# <a name="search-stlclr"></a>search (STL/CLR)
Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `search`. Pour plus d’informations, consultez [recherche](../standard-library/algorithm-functions.md#search).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)