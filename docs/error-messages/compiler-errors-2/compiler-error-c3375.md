---
title: Erreur du compilateur C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: ba1dbf08fb56364d2ab5b8c40847ab89484dc005
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781391"
---
# <a name="compiler-error-c3375"></a>Erreur du compilateur C3375

'fonction' : fonction déléguée ambiguë

Une instanciation de délégué aurait pu être pour une fonction membre static, ou comme délégué indépendant d’une fonction d’instance. Le compilateur a donc généré cette erreur.

Pour plus d’informations, consultez [delegate (Extensions du composant C++)](../../extensions/delegate-cpp-component-extensions.md).

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