---
title: Erreur du compilateur C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: f53312fa9225270ef79d50d2ad351adce790d6fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456288"
---
# <a name="compiler-error-c3367"></a>Erreur du compilateur C3367

'fonction_membre_statique' : impossible d’utiliser une fonction static pour créer un délégué indépendant

Quand vous appelez un délégué indépendant, vous devez passer une instance d’un objet. Dans la mesure où une fonction membre statique est appelée par le nom de classe, vous ne pouvez instancier un délégué indépendant qu’avec une fonction membre d’instance.

Pour plus d’informations sur les délégués indépendants, consultez [Comment : définir et utiliser délègue (C++ / c++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3367.

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```