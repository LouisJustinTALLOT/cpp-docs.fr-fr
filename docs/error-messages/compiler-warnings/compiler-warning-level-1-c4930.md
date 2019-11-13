---
title: Avertissement du compilateur (niveau 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: b21cc6364692eb2f3b1d56b03d175df1f2ad7ee8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050282"
---
# <a name="compiler-warning-level-1-c4930"></a>Avertissement du compilateur (niveau 1) C4930

'prototype' : fonction prototypée non appelée (une définition de variable est-elle prévue ?)

Le compilateur a détecté un prototype de fonction inutilisé. Si le prototype était conçu comme une déclaration de variable, supprimez les parenthèses ouvrantes/fermantes.

L’exemple suivant génère l’C4930 :

```cpp
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 peut également se produire lorsque le compilateur ne peut pas faire la distinction entre une déclaration de prototype de fonction et un appel de fonction.

L’exemple suivant génère l’C4930 :

```cpp
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

Dans l’exemple ci-dessus, le résultat d’une méthode qui accepte des arguments nuls est passé comme argument au constructeur d’une variable de classe locale sans nom. L’appel peut être enlevée en nommant la variable locale ou en préfixant l’appel de méthode avec une instance d’objet, ainsi que l’opérateur pointeur vers membre approprié.