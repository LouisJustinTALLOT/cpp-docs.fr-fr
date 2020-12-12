---
description: 'En savoir plus sur : l’utilisation du nom de fonction sans () ne génère pas de code'
title: L'utilisation d'un nom de fonction sans () ne génère pas de code
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 1fedc296422a759878c26469ccc20955043b3913
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277256"
---
# <a name="using-function-name-without--produces-no-code"></a>L'utilisation d'un nom de fonction sans () ne génère pas de code

Lorsqu’un nom de fonction déclaré dans votre programme est utilisé sans parenthèses, le compilateur ne produit pas de code. Cela se produit indépendamment du fait que la fonction accepte ou non les paramètres, car le compilateur calcule l’adresse de la fonction ; Toutefois, étant donné que l’opérateur d’appel de fonction « () » n’est pas présent, aucun appel n’est effectué. Ce résultat est similaire à ce qui suit :

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

Dans Visual C++, même si vous utilisez le niveau d’avertissement 4, aucune sortie de diagnostic n’est générée. Aucun avertissement n’est émis ; aucun code n’est produit.

L’exemple de code ci-dessous compile (avec un avertissement) et se lie correctement sans erreur, mais ne produit pas de code dans la référence à `funcn( )` . Pour que cela fonctionne correctement, ajoutez l’opérateur d’appel de fonction « () ».

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

[Optimisation de votre code](optimizing-your-code.md)
