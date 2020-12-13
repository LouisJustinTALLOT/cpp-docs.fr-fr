---
description: 'En savoir plus sur : erreur du compilateur C3375'
title: Erreur du compilateur C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: d2a9e9904185877e730096d08cb1f7c23c35c0d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335009"
---
# <a name="compiler-error-c3375"></a>Erreur du compilateur C3375

'fonction' : fonction déléguée ambiguë

Une instanciation de délégué aurait pu être pour une fonction membre static, ou comme délégué indépendant d’une fonction d’instance. Le compilateur a donc généré cette erreur.

Pour plus d’informations, consultez [Delegate (extensions du composant C++)](../../extensions/delegate-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3375.

```cpp
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
