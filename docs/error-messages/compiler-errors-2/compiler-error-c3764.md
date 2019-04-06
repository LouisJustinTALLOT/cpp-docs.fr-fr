---
title: Erreur du compilateur C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 2570ee9abb148b919242de7786cd6fa91765286f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773578"
---
# <a name="compiler-error-c3764"></a>Erreur du compilateur C3764

'fonction_substitution' : ne peut pas substituer la méthode de classe de base 'fonction_classe_base'

Le compilateur a détecté une substitution incorrecte. Par exemple, la fonction de la classe de base n’était pas `virtual`. Pour plus d’informations, consultez [remplacer](../../extensions/override-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3764.

```
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

## <a name="example"></a>Exemple

C3764 peut également se produire lorsqu’une méthode de classe de base est à la fois explicitement et nommé substitution. L’exemple suivant génère C3764.

```
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```