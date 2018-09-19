---
title: Erreur du compilateur C2676 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2676
dev_langs:
- C++
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2384970a59d8a13f18ff2d85144a991477b85457
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077475"
---
# <a name="compiler-error-c2676"></a>Erreur du compilateur C2676

'opérateur' binaire : 'type' ne définit pas cet opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini

Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2676.

```
// C2676.cpp
// C2676 expected
struct C {
   C();
} c;

struct D {
   D();
   D operator >>( C& ){return * new D;}
   D operator <<( C& ){return * new D;}
} d;

struct E {
   // operator int();
};

int main() {
   d >> c;
   d << c;
   E e1, e2;
   e1 == e2;   // uncomment operator int in class E, then
               // it is OK even though neither E::operator==(E) nor
               // operator==(E, E) defined. Uses the conversion to int
               // and then the builtin-operator==(int, int)
}
```

## <a name="example"></a>Exemple

C2676 peut également se produire si vous tentez d’effectuer une opération arithmétique de pointeur sur le `this` pointeur d’un type référence.

Le `this` pointeur est de type handle dans un type référence. Pour plus d’informations, consultez [sémantiques de ce pointeur](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

L’exemple suivant génère l’erreur C2676.

```
// C2676_a.cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      Console::WriteLine("{0}", this + 3.3);   // C2676
      Console::WriteLine("{0}", this[3.3]);   // OK
   }
};

int main() {
   A ^ mya = gcnew A();
}
```