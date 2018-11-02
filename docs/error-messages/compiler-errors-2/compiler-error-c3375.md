---
title: Erreur du compilateur C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: b3dfc17f9df495fe6907b816bace0dac1eff08cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545273"
---
# <a name="compiler-error-c3375"></a>Erreur du compilateur C3375

'fonction' : fonction déléguée ambiguë

Une instanciation de délégué aurait pu être pour une fonction membre static, ou comme délégué indépendant d’une fonction d’instance. Le compilateur a donc généré cette erreur.

Pour plus d’informations, consultez [delegate (Extensions du composant C++)](../../windows/delegate-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3375.

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```