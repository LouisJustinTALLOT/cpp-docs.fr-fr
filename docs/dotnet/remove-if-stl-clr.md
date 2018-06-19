---
title: remove_if (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove_if
dev_langs:
- C++
helpviewer_keywords:
- remove_if function [STL/CLR]
ms.assetid: de501d3f-965b-4a99-b833-f6fa303fbcdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d481024679200c4c630dd6f739629937ea997db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161237"
---
# <a name="removeif-stlclr"></a>remove_if (STL/CLR)
Élimine d’une plage donnée les éléments qui répondent à un prédicat, sans modifier l’ordre des éléments restants et en retournant la fin d’une nouvelle plage exempte de la valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `remove_if`. Pour plus d’informations, consultez [remove_if](../standard-library/algorithm-functions.md#remove_if).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)