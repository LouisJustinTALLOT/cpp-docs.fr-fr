---
title: Avertissement du compilateur (niveau 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 4c92c23af4aeb6a18c812517cfef9fa00d15dfcb
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965390"
---
# <a name="compiler-warning-level-1-c4486"></a>Avertissement du compilateur (niveau 1) C4486

'fonction' : une méthode virtuelle privée d’une classe ref ou d’une classe value doit être marquée comme’sealed'

Étant donné qu’une fonction membre virtuelle privée d’une classe ou d’un struct managé n’est pas accessible ou substituée, elle doit être marquée comme [sealed](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4486.

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>Exemple

L’exemple suivant illustre une utilisation possible d’une fonction virtuelle scellée privée.

```cpp
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