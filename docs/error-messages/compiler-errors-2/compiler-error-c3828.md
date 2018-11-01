---
title: Erreur du compilateur C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 68a82105a2ff7d58090e9f345bf7aafb34d492d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515282"
---
# <a name="compiler-error-c3828"></a>Erreur du compilateur C3828

type d’objet : arguments de positionnement non autorisés pendant la création d’instances de gestion ou WinRTclasses

Lorsque vous créez un objet d’un type managé ou d’un type Windows Runtime, vous ne pouvez pas utiliser la forme positionnement de l’opérateur [gcnew nouvelle, ref](../../windows/ref-new-gcnew-cpp-component-extensions.md) ou [nouveau](../../cpp/new-operator-cpp.md).

L'exemple suivant génère l'erreur C3828 et montre comment la corriger :

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```