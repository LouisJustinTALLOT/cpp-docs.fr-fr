---
description: 'En savoir plus sur : erreur du compilateur C3367'
title: Erreur du compilateur C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: cd428bb0472ab9cb621f85ac684cbb4d9bbc12d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245276"
---
# <a name="compiler-error-c3367"></a>Erreur du compilateur C3367

'fonction_membre_statique' : impossible d’utiliser une fonction static pour créer un délégué indépendant

Quand vous appelez un délégué indépendant, vous devez passer une instance d’un objet. Dans la mesure où une fonction membre statique est appelée par le nom de classe, vous ne pouvez instancier un délégué indépendant qu’avec une fonction membre d’instance.

Pour plus d’informations sur les délégués indépendants, consultez Guide pratique [pour définir et utiliser des délégués (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

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
