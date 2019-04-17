---
title: Erreur du compilateur C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: f499bb2a8fd6d3148935daec89835b79d2ff5b49
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770549"
---
# <a name="compiler-error-c3828"></a>Erreur du compilateur C3828

type d’objet : arguments de positionnement non autorisés pendant la création d’instances de gestion ou WinRTclasses

Lorsque vous créez un objet d’un type managé ou d’un type Windows Runtime, vous ne pouvez pas utiliser la forme positionnement de l’opérateur [gcnew nouvelle, ref](../../extensions/ref-new-gcnew-cpp-component-extensions.md) ou [nouveau](../../cpp/new-operator-cpp.md).

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