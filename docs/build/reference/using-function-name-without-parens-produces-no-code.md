---
title: À l’aide du nom de fonction sans () ne génère pas de Code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40aed3969ae0707b07f0912d7247b49886d0319d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373980"
---
# <a name="using-function-name-without--produces-no-code"></a>L'utilisation d'un nom de fonction sans () ne génère pas de code
Lorsqu’un nom de fonction déclaré dans votre programme est utilisé sans parenthèses, le compilateur ne génère pas de code. Cela se produit, quelle que soit ou non la fonction accepte des paramètres, car le compilateur calcule l’adresse de la fonction ; Toutefois, étant donné que l’opérateur d’appel de fonction « () » n’est pas présent, aucun appel est effectué. Ce résultat est similaire à ce qui suit :  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 Dans Visual C++, même en utilisant le niveau d’avertissement 4 ne génère aucune sortie de diagnostic. Aucun avertissement n’est émis ; Aucun code n’est généré.  
  
 L’exemple de code ci-dessous compilé (avec un avertissement) et lié correctement sans erreurs, mais génère pas de code dans la référence à `funcn( )`. Pour que cela fonctionne correctement, ajoutez l’opérateur d’appel de fonction « () ».  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation du code](../../build/reference/optimizing-your-code.md)