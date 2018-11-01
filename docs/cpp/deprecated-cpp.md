---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 34f9c10cd898b0359463d5933141822576fa4a11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485850"
---
# <a name="deprecated-c"></a>deprecated (C++)

Cette rubrique concerne le spécifiques à Microsoft déconseillé declspec déclaration. Pour plus d’informations sur C ++ 14 `[[deprecated]]` attribut et des conseils sur l’utilisation de cet attribut et le declspec de spécifique à Microsoft ou le pragma, consultez [attributs Standard C++](attributes.md).

Avec les exceptions indiquées ci-dessous, le **déconseillée** déclaration offre les mêmes fonctionnalités que le [déconseillée](../preprocessor/deprecated-c-cpp.md) pragma :

- Le **déconseillée** déclaration vous permet de spécifier des formes particulières de surcharges de fonction comme étant déconseillés, alors que la forme pragma s’applique à toutes les formes surchargées d’un nom de fonction.

- Le **déconseillée** déclaration vous permet de spécifier un message qui s’affiche au moment de la compilation. Le texte du message peut être issu d'une macro.

- Les macros ne peuvent être marquées comme déconseillées que via le **déconseillée** pragma.

Si le compilateur détecte l’utilisation d’un identificateur déconseillé ou la norme [ `[[deprecated]]` ](attributes.md) attribut, un [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) avertissement est levé.

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