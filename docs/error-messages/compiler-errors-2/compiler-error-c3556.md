---
title: Erreur du compilateur C3556
ms.date: 11/04/2016
f1_keywords:
- C3556
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
ms.openlocfilehash: 50f97c4360080f1271d9decc3b3460c06f3fec0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230816"
---
# <a name="compiler-error-c3556"></a>Erreur du compilateur C3556

> '*expression*' : argument incorrect pour’decltype'

Le compilateur ne peut pas déduire le type de l’expression qui est l’argument du spécificateur de type d' `decltype(` *expression* `)` .

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, le compilateur ne peut pas déduire le type de l’argument `myFunction` car `myFunction` est surchargé. Pour résoudre ce problème, vous pouvez utiliser **`static_cast`** pour créer une instance d’un pointeur vers la fonction surchargée particulière à spécifier dans l' **`decltype`** expression.

```cpp
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);
void myFunction(float, float);

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) {
    std::cout << "called myFunction(" << i << ")" << std::endl;
}

void myFunction(float f, float g) {
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl;
}

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```
