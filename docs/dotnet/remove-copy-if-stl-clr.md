---
title: remove_copy_if (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove_copy_if
dev_langs:
- C++
helpviewer_keywords:
- remove_copy_if function [STL/CLR]
ms.assetid: 5307f5fe-b6bb-4968-8da1-fea84ab96655
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1059916855822dcdc0fd2e17e15cf95cfab4d257
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163316"
---
# <a name="removecopyif-stlclr"></a>remove_copy_if (STL/CLR)
Copie les éléments d'une plage source vers une plage de destination. Les éléments répondant à un prédicat ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `remove_copy_if`. Pour plus d’informations, consultez [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)