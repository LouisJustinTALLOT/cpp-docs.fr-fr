---
title: max (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::max
dev_langs:
- C++
helpviewer_keywords:
- max function [STL/CLR]
ms.assetid: bf51aedc-b7a0-4b6c-a76e-fdbc4af042fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0d06044fd8996682431be0f2fd89ae3059c93f51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133218"
---
# <a name="max-stlclr"></a>max (STL/CLR)
Compare deux objets et retourne le plus grand des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `max`. Pour plus d’informations, consultez [max](../standard-library/algorithm-functions.md#max).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)