---
title: Avertissement du compilateur (niveau 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 402d5eefde6c2dfd5693e53c27edb00d1ac2e56c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780208"
---
# <a name="compiler-warning-level-1-c4486"></a>Avertissement du compilateur (niveau 1) C4486

'fonction' : une méthode virtuelle privée d’une classe ref ou d’une classe value doit être marquée comme 'sealed'

Dans la mesure où une fonction membre virtuelle privée d’une classe managée ou un struct ne peut pas être accessible ou de substitution, il doit être marqué [sealed](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4486.

```
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>Exemple

L’exemple suivant montre une utilisation possible d’une fonction sealed, virtual private.

```
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```