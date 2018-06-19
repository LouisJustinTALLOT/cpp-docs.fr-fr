---
title: Compilateur avertissement (niveau 4) C4130 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 226b715689e506cb34ea6e7684f9ddcf041e638b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292173"
---
# <a name="compiler-warning-level-4-c4130"></a>Avertissement du compilateur (niveau 4) C4130
'opérateur' : opération logique sur l’adresse d’une constante de chaîne  
  
 L’utilisation de l’opérateur avec l’adresse d’un littéral de chaîne génère du code inattendu.  
  
 L’exemple suivant génère l’avertissement C4130 :  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 L’ instruction **If** compare la valeur stockée dans le pointeur `pc` à l’adresse de la chaîne « Hello », qui est allouée séparément à chaque occurrence de la chaîne dans le code. L’ instruction **If** ne compare pas la chaîne vers laquelle `pc` pointe avec la chaîne « Hello ».  
  
 Pour comparer des chaînes, utilisez la fonction `strcmp` .