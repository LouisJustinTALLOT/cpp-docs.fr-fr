---
title: Avertissement du compilateur (niveau 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 15cd1ed61c747e2c9168b9fc0fee03dca8403a24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242784"
---
# <a name="compiler-warning-level-1-c4930"></a>Avertissement du compilateur (niveau 1) C4930

'prototype' : fonction prototypée non appelée (était une définition de variable souhaitée ?)

Le compilateur a détecté un prototype de fonction non utilisées. Si le prototype a été conçu comme une déclaration de variable, supprimez les parenthèses d’ouverture/fermeture.

L’exemple suivant génère l’erreur C4930 :

```
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

L’exemple suivant génère l’erreur C4930 :

```
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

Dans l’exemple ci-dessus, le résultat d’une méthode qui n’accepte aucun argument est passé en tant qu’argument au constructeur d’une variable de classe locale sans nom. L’appel peut être éviter toute ambiguïté en nommant la variable locale ou en faisant précéder l’appel de méthode avec une instance d’objet, ainsi que l’opérateur pointeur vers membre approprié.