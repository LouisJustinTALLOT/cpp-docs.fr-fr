---
description: 'En savoir plus sur : erreur du compilateur C3154'
title: Erreur du compilateur C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: c43800aba54431041b13e70d9e94c80d98d8ee84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203976"
---
# <a name="compiler-error-c3154"></a>Erreur du compilateur C3154

', 'Attendu avant les points de suspension. Points de suspension séparés par des virgules non pris en charge dans les fonctions de tableau de paramètres.

Une fonction d’argument de variable n’a pas été déclarée correctement.

Pour plus d’informations, consultez [listes d’arguments de variables (...) (C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3154.

```cpp
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```
