---
title: __if_exists, instruction
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: 6522b1877dd2517032fc140de42671353ce9c357
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561399"
---
# <a name="__if_exists-statement"></a>__if_exists, instruction

L' **`__if_exists`** instruction vérifie si l’identificateur spécifié existe. Si l'identificateur existe, le bloc d'instructions spécifié est exécuté.

## <a name="syntax"></a>Syntaxe

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Paramètres

*identificateur*\
Identificateur dont vous voulez tester l'existence.

*publication*\
Une ou plusieurs instructions à exécuter si l' *identificateur* existe.

## <a name="remarks"></a>Notes

> [!CAUTION]
> Pour obtenir les résultats les plus fiables, utilisez l' **`__if_exists`** instruction sous les contraintes suivantes.

- Appliquez l' **`__if_exists`** instruction uniquement aux types simples, et non aux modèles.

- Appliquez l' **`__if_exists`** instruction aux identificateurs à l’intérieur ou à l’extérieur d’une classe. N’appliquez pas l' **`__if_exists`** instruction à des variables locales.

- Utilisez l' **`__if_exists`** instruction uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, l' **`__if_exists`** instruction peut tester uniquement des types entièrement définis.

- Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.

Le complément de l' **`__if_exists`** instruction est l’instruction [__if_not_exists](../cpp/if-not-exists-statement.md) .

## <a name="example"></a>Exemple

Notez que cet exemple utilise des modèles, ce qui n'est pas recommandé.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Output

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Instruction __if_not_exists](../cpp/if-not-exists-statement.md)
