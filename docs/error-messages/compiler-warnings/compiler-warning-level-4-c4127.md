---
title: Avertissement du compilateur (niveau 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 52a966bb321226058afbf4667a4192e4e814f0a1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075853"
---
# <a name="compiler-warning-level-4-c4127"></a>Avertissement du compilateur (niveau 4) C4127

> l'expression conditionnelle est une constante

## <a name="remarks"></a>Notes

L’expression de contrôle d’une instruction **If** ou d’une boucle **while** prend la valeur d’une constante. En raison de leur utilisation idiomatique courante, à compter de Visual Studio 2015 Update 3, les constantes triviales telles que 1 ou **true** ne déclenchent pas l’avertissement, à moins qu’elles ne soient le résultat d’une opération dans une expression.

Si l’expression de contrôle d’une boucle **while** est une constante parce que la boucle se termine au milieu, envisagez de remplacer la boucle **while** par une boucle **for** . Vous pouvez omettre l’initialisation, le test de fin et l’incrément de boucle d’une boucle **for** , ce qui entraîne une boucle infinie, tout comme `while(1)`, et vous pouvez quitter la boucle à partir du corps de l’instruction **for** .

## <a name="example"></a>Exemple

L’exemple suivant montre deux façons de générer C4127 et montre comment utiliser une boucle for pour éviter l’avertissement :

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

Cet avertissement peut également être généré quand une constante au moment de la compilation est utilisée dans une expression conditionnelle :

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```