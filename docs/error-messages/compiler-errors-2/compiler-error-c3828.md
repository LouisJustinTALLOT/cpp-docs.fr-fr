---
description: 'En savoir plus sur : erreur du compilateur C3828'
title: Erreur du compilateur C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 90c731ffc636355b5c9a1963facbcccabf356700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249319"
---
# <a name="compiler-error-c3828"></a>Erreur du compilateur C3828

'Object type' : arguments de positionnement non autorisés lors de la création d’instances de Managed ou WinRTclasses

Lors de la création d’un objet d’un type managé ou d’un type de Windows Runtime, vous ne pouvez pas utiliser la forme de placement de Operator [ref New, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) ou [New](../../cpp/new-operator-cpp.md).

L'exemple suivant génère l'erreur C3828 et montre comment la corriger :

```cpp
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
