---
description: 'En savoir plus sur : déconseillé (C++)'
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: cd7bc3acbe6a61e87a1766025bcc174268190c48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339421"
---
# <a name="deprecated-c"></a>deprecated (C++)

Cette rubrique concerne la déclaration declspec déconseillée spécifique à Microsoft. Pour plus d’informations sur l’attribut C++ 14 et pour savoir `[[deprecated]]` quand utiliser cet attribut ou le declspec ou pragma spécifique à Microsoft, consultez [attributs standard c++](attributes.md).

Avec les exceptions indiquées ci-dessous, la **`deprecated`** déclaration offre les mêmes fonctionnalités que le pragma [déconseillé](../preprocessor/deprecated-c-cpp.md) :

- La **`deprecated`** déclaration vous permet de spécifier des formes particulières de surcharges de fonction comme dépréciées, tandis que la forme de pragma s’applique à toutes les formes surchargées d’un nom de fonction.

- La **`deprecated`** déclaration vous permet de spécifier un message qui s’affichera au moment de la compilation. Le texte du message peut être issu d'une macro.

- Les macros peuvent uniquement être marquées comme déconseillées avec le **`deprecated`** pragma.

Si le compilateur rencontre l’utilisation d’un identificateur déconseillé ou de l' [`[[deprecated]]`](attributes.md) attribut standard, un avertissement [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) est levé.

## <a name="examples"></a>Exemples

L'exemple suivant montre comment marquer des fonctions comme déconseillés, et comment spécifier un message à afficher au moment de la compilation, lorsque la fonction déconseillée est utilisée.

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

L'exemple suivant montre comment marquer des classes comme déconseillés, et comment spécifier un message à afficher au moment de la compilation, lorsque la classe déconseillée est utilisée.

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
