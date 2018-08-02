---
title: True (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb810f880ac86651059d71a59040e34810c7e167
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464770"
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>Notes  
 Ce mot clé est une des deux valeurs d’une variable de type [bool](../cpp/bool-cpp.md) ou une expression conditionnelle (une expression conditionnelle est maintenant une véritable expression booléenne). Si `i` est de type **bool**, puis l’instruction `i = true;` attribue **true** à `i`.  
  
## <a name="example"></a>Exemple  
  
```cpp 
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)