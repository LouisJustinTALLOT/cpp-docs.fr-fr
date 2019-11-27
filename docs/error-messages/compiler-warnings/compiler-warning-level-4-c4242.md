---
title: Avertissement du compilateur (niveau 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 3123a414dc7a169d2a472dad96d659a9e56c9020
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541752"
---
# <a name="compiler-warning-level-4-c4242"></a>Avertissement du compilateur (niveau 4) C4242

'identificateur' : conversion de’type1 'en’type2 ', perte possible de données

Les types sont différents. La conversion de type peut entraîner une perte de données. Le compilateur effectue la conversion de type.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

Pour plus d’informations sur C4242, consultez [Erreurs de compilateur courantes](/windows/win32/WinProg64/common-compiler-errors).

L’exemple suivant génère l’C4242 :

```cpp
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```