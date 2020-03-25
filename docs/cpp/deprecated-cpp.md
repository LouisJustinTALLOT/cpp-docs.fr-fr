---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189479"
---
# <a name="deprecated-c"></a>deprecated (C++)

Cette rubrique concerne la déclaration declspec déconseillée spécifique à Microsoft. Pour plus d’informations sur l’attribut `[[deprecated]]` de c++ 14, ainsi que des conseils sur l’utilisation de cet attribut ou du pragma declspec ou Microsoft spécifique, consultez [ C++ attributs standard](attributes.md).

Avec les exceptions indiquées ci-dessous, la Déclaration **déconseillée** offre les mêmes fonctionnalités que le pragma [déconseillé](../preprocessor/deprecated-c-cpp.md) :

- La Déclaration **déconseillée** vous permet de spécifier des formes particulières de surcharges de fonction comme dépréciées, tandis que la forme de pragma s’applique à toutes les formes surchargées d’un nom de fonction.

- La Déclaration **déconseillée** vous permet de spécifier un message qui s’affichera au moment de la compilation. Le texte du message peut être issu d'une macro.

- Les macros ne peuvent être marquées comme dépréciées qu’avec le pragma **déconseillé** .

Si le compilateur rencontre l’utilisation d’un identificateur déconseillé ou de l’attribut [`[[deprecated]]`](attributes.md) standard, un avertissement [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) est levé.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

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
