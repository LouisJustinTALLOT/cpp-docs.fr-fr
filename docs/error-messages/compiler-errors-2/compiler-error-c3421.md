---
title: Erreur du compilateur C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 39a57aa7b85b9f8a8aae0b93e2b346584edef8de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756238"
---
# <a name="compiler-error-c3421"></a>Erreur du compilateur C3421

'type' : vous ne pouvez pas appeler le finaliseur de cette classe, car il est soit inaccessible, soit inexistant

Un finaliseur est implicitement privé. Il ne peut donc pas être appelé en dehors de son type englobant.

Pour plus d’informations, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommer des classes et desC++structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3421.

```cpp
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```
