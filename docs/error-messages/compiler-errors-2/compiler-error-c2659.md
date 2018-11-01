---
title: Erreur du compilateur C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: b8b6493b01ac2b88ea50ba50157328f59fdbedf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601654"
---
# <a name="compiler-error-c2659"></a>Erreur du compilateur C2659

'opérateur' : fonction comme opérande gauche

Une fonction se trouvait sur le côté gauche de l'opérateur spécifié. En règle générale, cette erreur est due au fait que le compilateur a analysé l'identificateur situé à gauche de l'opérateur en tant que fonction alors que le développeur le destinait à être une variable. Pour plus d’informations, consultez Wikipedia article [analyse plus ennuyeux](http://en.wikipedia.org/wiki/Most_vexing_parse). Cet exemple montre une déclaration de fonction et une définition de variable qui sont faciles à confondre :

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

Pour résoudre ce problème, modifiez la déclaration de l'identificateur afin qu'il ne soit pas analysé comme une déclaration de fonction.

L'erreur C2659 peut également se produire lorsque la fonction comporte un type qui ne peut pas être utilisé dans l'expression à gauche de l'opérateur spécifié. Cet exemple génère l'erreur C2659 lorsque le code assigne un pointeur de fonction à une fonction :

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```