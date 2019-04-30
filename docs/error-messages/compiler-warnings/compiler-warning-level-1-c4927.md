---
title: Avertissement du compilateur (niveau 1) C4927
ms.date: 11/04/2016
f1_keywords:
- C4927
helpviewer_keywords:
- C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
ms.openlocfilehash: 59a39e4e695fdd161135cd70a74e1f3f6518e361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393452"
---
# <a name="compiler-warning-level-1-c4927"></a>Avertissement du compilateur (niveau 1) C4927

conversion non conforme ; plusieurs conversions définies par l’utilisateur ont été appliquées implicitement

Plusieurs conversions définies par l’utilisateur sont implicitement appliquée à une valeur unique, le compilateur n’a pas trouvé une conversion explicite mais a trouvé une conversion, il est utilisé.

L’exemple suivant génère l’erreur C4927 :

```
// C4927.cpp
// compile with: /W1
struct B
{
   operator int ()
   {
      return 0;
   }
};

struct A
{
   A(int i)
   {
   }

   /*
   // uncomment this constructor to resolve
   A(B b)
   {
   }
   */
};

A f1( B& b)
{
   return A(b);
}

B& f2( B& b)
{
   return b;
}

A f()
{
   B b;
   return A(b);   // ok
   return f1(b);  // ok
   return b;      // C4927
   return B(b);   // C4927
   return f2(b);  // C4927
}

int main()
{
   B b;
   A a = b;
   A a2(b);
}
```