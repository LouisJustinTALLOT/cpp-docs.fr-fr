---
description: 'En savoir plus sur : erreur du compilateur C3628'
title: Erreur du compilateur C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: ed0c434a40e6c513580e37b5fb2fc9f44b1dc5dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144402"
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
