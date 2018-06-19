---
title: Compilateur avertissement (niveau 1) C4750 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffe378f8d2466e702c90127e44f3b48831abf50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282442"
---
# <a name="compiler-warning-level-1-c4750"></a>Avertissement du compilateur (niveau 1) C4750
'identifier' : fonction with _alloca() inline dans une boucle  
  
 La fonction 'identifier' force l’expansion inline de la fonction [_alloca](../../c-runtime-library/reference/alloca.md) dans une boucle, ce qui peut provoquer un dépassement de capacité de la pile lors de l’exécution de la boucle.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez que la fonction 'identifier' n’est pas modifiée avec le spécificateur [__forceinline](../../cpp/inline-functions-cpp.md) .  
  
2.  Veillez à ce que la fonction 'identifier' ne contienne pas une fonction [_alloca](../../c-runtime-library/reference/alloca.md) contenue elle-même dans une boucle.  
  
3.  Ne spécifiez pas le commutateur de compilation [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md)ni [/Og](../../build/reference/og-global-optimizations.md) .  
  
4.  Placez la fonction [_alloca](../../c-runtime-library/reference/alloca.md) dans une [instruction try-except](../../cpp/try-except-statement.md) qui intercepte un dépassement de capacité de la pile.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant appelle `MyFunction` dans une boucle, et `MyFunction` appelle la fonction `_alloca` . Le modificateur `__forceinline` provoque l’expansion inline de la fonction `_alloca` .  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [_alloca](../../c-runtime-library/reference/alloca.md)