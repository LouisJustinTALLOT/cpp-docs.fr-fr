---
description: 'En savoir plus sur : pragma déconseillé'
title: deprecated (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: b3f7e8bf17e98f6e6f57511f3c0c9a94a9388bf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300773"
---
# <a name="deprecated-pragma"></a>deprecated (pragma)

Le **`deprecated`** pragma vous permet d’indiquer qu’une fonction, un type ou tout autre identificateur ne peut plus être pris en charge dans une version ultérieure ou qu’il ne doit plus être utilisé.

> [!NOTE]
> Pour plus d’informations sur l' `[[deprecated]]` attribut C++ 14 et des conseils sur l’utilisation de cet attribut au lieu du `__declspec(deprecated)` modificateur Microsoft ou du **`deprecated`** pragma, consultez [attributs en C++](../cpp/attributes.md).

## <a name="syntax"></a>Syntaxe

> **#pragma déconseillé (** *identificateur1* [ **,** *identificateur2* ...] **)**

## <a name="remarks"></a>Notes

Lorsque le compilateur rencontre un identificateur spécifié par un **`deprecated`** pragma, il émet un avertissement du compilateur [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Vous pouvez désapprouver des noms de macros. Placez le nom de la macro entre guillemets, sinon une expansion macro va se produire.

Étant donné que le **`deprecated`** pragma fonctionne sur tous les identificateurs correspondants et qu’il ne prend pas en compte les signatures, il ne s’agit pas de la meilleure option pour déprécier des versions spécifiques des fonctions surchargées. Tout nom de fonction mis en correspondance qui est placé dans la portée déclenche l’avertissement.

Nous vous recommandons d’utiliser l’attribut C++ 14 `[[deprecated]]` , lorsque cela est possible, au lieu du **`deprecated`** pragma. Le modificateur de déclaration __declspec spécifique à Microsoft [(déconseillé)](../cpp/deprecated-cpp.md) est également un meilleur choix dans de nombreux cas que le **`deprecated`** pragma. L' `[[deprecated]]` attribut et le `__declspec(deprecated)` modificateur vous permettent de spécifier l’État déconseillé pour des formes particulières de fonctions surchargées. L’avertissement de diagnostic apparaît uniquement sur les références à la fonction surchargée spécifique à laquelle s’applique l’attribut ou le modificateur.

## <a name="example"></a>Exemple

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

L'exemple suivant montre comment déconseiller une classe :

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
