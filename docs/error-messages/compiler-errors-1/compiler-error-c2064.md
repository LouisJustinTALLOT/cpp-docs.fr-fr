---
description: 'En savoir plus sur : erreur du compilateur C2064'
title: Erreur du compilateur C2064
ms.date: 11/04/2016
f1_keywords:
- C2064
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
ms.openlocfilehash: dd9f0386267a81d4f92d6dd0474cd9a3292e7345
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328569"
---
# <a name="compiler-error-c2064"></a>Erreur du compilateur C2064

le terme ne correspond pas à une fonction qui prend N arguments

Un appel est passé à une fonction via une expression. L'expression ne correspond pas à un pointeur vers une fonction qui accepte le nombre spécifié d'arguments.

Dans cet exemple, le code tente d'appeler des éléments autres que des fonctions en tant que fonctions. L'exemple suivant génère l'erreur C2064 :

```cpp
// C2064.cpp
int i, j;
char* p;
void func() {
   j = i();    // C2064, i is not a function
   p();        // C2064, p doesn't point to a function
}
```

Vous devez appeler des pointeurs vers des fonctions membres non static à partir du contexte d'une instance d'objet. L'exemple suivant génère l'erreur C2064 et montre comment la corriger :

```cpp
// C2064b.cpp
struct C {
   void func1(){}
   void func2(){}
};

typedef void (C::*pFunc)();

int main() {
   C c;
   pFunc funcArray[2] = {&C::func1, &C::func2};
   (funcArray[0])();    // C2064
   (c.*funcArray[0])(); // OK - function called in instance context
}
```

Dans une classe, les pointeurs fonction membre doivent également indiquer le contexte de l'objet appelant. L'exemple suivant génère l'erreur C2064 et montre comment la corriger :

```cpp
// C2064d.cpp
// Compile by using: cl /c /W4 C2064d.cpp
struct C {
   typedef void (C::*pFunc)();
   pFunc funcArray[2];
   void func1(){}
   void func2(){}
   C() {
      funcArray[0] = &C::func1;
      funcArray[1] = &C::func2;
   }
   void func3() {
      (funcArray[0])();   // C2064
      (this->*funcArray[0])(); // OK - called in this instance context
   }
};
```
