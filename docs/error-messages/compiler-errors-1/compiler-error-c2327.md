---
title: Erreur du compilateur C2327 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2327
dev_langs:
- C++
helpviewer_keywords:
- C2327
ms.assetid: 95278c95-d1f9-4487-ad27-53311f5e8112
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d8b5b0172d73ab76eb9500dddc6dfe264064ccd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097950"
---
# <a name="compiler-error-c2327"></a>Erreur du compilateur C2327

'symbol' : n’est pas un nom de type, statique ou énumérateur

Le code dans une classe imbriquée tente d’accéder à un membre de la classe englobante qui n’est pas un nom de type, un membre statique ou un énumérateur.

Lors de la compilation avec **/CLR**, une cause courante C2327 est une propriété portant le même nom que le type de propriété.

L’exemple suivant génère l’erreur C2327 :

```
// C2327.cpp
int x;
class enclose {
public:
   int x;
   static int s;
   class inner {
      void f() {
         x = 1;   // C2327; enclose::x is not static
         s = 1;   // ok; enclose::s is static
         ::x = 1;   // ok; ::x refers to global
      }
   };
};
```

C2327 peut également se produire si le nom d’un type est masqué par le nom d’un membre :

```
// C2327b.cpp
class X {};

class S {
   X X;
   // try the following line instead
   // X MyX;
   X other;   // C2327, rename member X
};
```

C2327 peut également se déclencher dans ce cas, où vous avez besoin pour spécifier complètement le type de données du paramètre :

```
// C2327c.cpp
// compile with: /c
struct A {};

struct B {
   int A;
   void f(A a) {   // C2327
   void f2(struct A a) {}   // OK
   }
};
```

L’exemple suivant génère l’erreur C2327 :

```
// C2327d.cpp
// compile with: /clr /c
using namespace System;

namespace NA {
   public enum class E : Int32 {
      one = 1,
      two = 2,
      three = 3
   };

   public ref class A {
   private:
      E m_e;
   public:
      property E E {
         NA::E get() {
            return m_e;
         }
         // At set, compiler doesn't know whether E is get_E or
         // Enum E, therefore fully qualifying Enum E is necessary
         void set( E e ) {   // C2327
            // try the following line instead
            // void set(NA::E e) {
            m_e = e;
         }
      }
   };
}
```

L’exemple suivant montre C2327 lorsqu’une propriété a le même nom que le type de propriété :

```
// C2327f.cpp
// compile with: /clr /c
public value class Address {};

public ref class Person {
public:
   property Address Address {
      ::Address get() {
         return address;
      }
      void set(Address addr) {   // C2327
      // try the following line instead
      // set(::Address addr) {
         address = addr;
      }
   }
private:
   Address address;   // C2327
   // try the following line instead
   // ::Address address;
};
```
