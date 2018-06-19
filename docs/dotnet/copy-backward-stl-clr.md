---
title: copy_backward (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::copy_backward
dev_langs:
- C++
helpviewer_keywords:
- copy_backward function [STL/CLR]
ms.assetid: 649db3fd-5a79-44b6-bea9-ecbcbeba1f32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5ff5b52b356d4601ac671f148a4b0464f69f3a16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104670"
---
# <a name="copybackward-stlclr"></a>copy_backward (STL/CLR)
Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions vers le haut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction comporte comme la fonction de la bibliothèque Standard C++ `copy_backward`. Pour plus d’informations, consultez [copy_backward](../standard-library/algorithm-functions.md#copy_backward).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)