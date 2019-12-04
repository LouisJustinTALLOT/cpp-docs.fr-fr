---
title: Erreur du compilateur C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755822"
---
# <a name="compiler-error-c3628"></a>Erreur du compilateur C3628

'classe de base' : Managed ou WinRTclasses prend uniquement en charge l’héritage public

Une tentative d’utilisation d’une classe managée ou WinRT en tant que classe de base [privée](../../cpp/private-cpp.md) ou [protégée](../../cpp/protected-cpp.md) a été effectuée. Une classe managée ou WinRT ne peut être utilisée qu’en tant que classe de base avec un accès [public](../../cpp/public-cpp.md) .

L'exemple suivant génère l'erreur C3628 et montre comment la corriger :

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
