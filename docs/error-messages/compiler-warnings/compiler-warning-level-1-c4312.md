---
title: Compilateur avertissement (niveau 1) C4312 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4312
dev_langs:
- C++
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18039e44a5616330c66603e448bcafd6d18ff7aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279673"
---
# <a name="compiler-warning-level-1-c4312"></a>Avertissement du compilateur (niveau 1) C4312
'opération' : la conversion de 'type1' en 'type2' d'une taille supérieure  
  
 Cet avertissement détecte une tentative d'attribuer une valeur 32 bits à un type pointeur 64 bits, par exemple, en convertissant une valeur `int` ou `long` 32 bits en pointeur 64 bits.  
  
 Cette conversion est potentiellement dangereuse, même pour des valeurs de pointeur qui tiennent dans 32 bits quand une extension de signe intervient. Si un entier 32 bits négatif est attribué à un type pointeur 64 bits, l'extension de signe se produit et la valeur de pointeur fait référence à une adresse mémoire différente de la valeur de l'entier.  
  
 Cet avertissement est émis uniquement pour les cibles de compilation 64 bits. Pour plus d’informations, consultez [les règles d’utilisation des pointeurs](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 L'exemple de code suivant génère l'erreur C4312 quand il est compilé pour des cibles 64 bits :  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```