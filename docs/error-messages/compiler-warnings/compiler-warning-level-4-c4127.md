---
title: Compilateur avertissement (niveau 4) C4127 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80f831d527e918fce0551f6a1336fd2fe994917d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161279"
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