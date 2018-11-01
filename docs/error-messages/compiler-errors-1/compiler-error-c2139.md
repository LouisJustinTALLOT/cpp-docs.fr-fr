---
title: Erreur du compilateur C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: f462b7d26e21b9313949bb3968b5b39e81bb30b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437125"
---
# <a name="compiler-error-c2139"></a>Erreur du compilateur C2139

'type' : une classe non définie n’est pas autorisée en tant qu’argument pour un trait de type intrinsèque du compilateur 'trait'

Un argument non valide a été passé à un trait de type.

Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2139.

```
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```