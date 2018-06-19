---
title: Compilateur avertissement (niveau 1) C4313 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e42bd8f19ac9a70f93a26265af6e310fb51e7229
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283937"
---
# <a name="compiler-warning-level-1-c4313"></a>Avertissement du compilateur (niveau 1) C4313
’fonction’ : conflit entre ’spécificateur de format’ dans la chaîne de format et l’argument nombre de type ’type’  
  
 Il existe un conflit entre le format spécifié et la valeur que vous transmettez. Par exemple, vous avez transmis un paramètre 64 bits à un spécificateur de format %d non qualifié qui attend un paramètre entier 32 bits. Cet avertissement est uniquement en vigueur quand le code est compilé pour des cibles 64 bits.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant génère l'avertissement C4313 quand il est compilé pour une cible 64 bits.  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```