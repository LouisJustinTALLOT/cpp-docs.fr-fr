---
title: Avertissement du compilateur (niveau 4) C4127
ms.date: 09/13/2018
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 7f1e23d15d8daa126987278611cb5a85a5a36fc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401308"
---
# <a name="compiler-warning-level-4-c4127"></a>Avertissement du compilateur (niveau 4) C4127

> l'expression conditionnelle est une constante

## <a name="remarks"></a>Notes

Expression de contrôle d’un **si** instruction ou **tandis que** boucle correspond à une constante. En raison de leur utilisation IDIOMATIQUE courants, à compter de Visual Studio 2015 update 3, constantes triviales par exemple, 1 ou **true** ne déclenchent pas l’avertissement, sauf s’ils sont le résultat d’une opération dans une expression.

Si l’expression de contrôle d’un **tandis que** boucle est une constante, car la boucle s’arrête au milieu, envisagez de remplacer le **tandis que** boucle avec une **pour** boucle. Vous pouvez omettre l’initialisation, le test de fin et l’incrément de boucle d’un **pour** boucle, ce qui entraîne une boucle infinie, tout comme `while(1)`, et vous pouvez quitter la boucle à partir du corps de la **pour** instruction.

## <a name="example"></a>Exemple

L’exemple suivant montre deux façons C4127 est généré et montre comment utiliser une boucle éviter l’avertissement :

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```