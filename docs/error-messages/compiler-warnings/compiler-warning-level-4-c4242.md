---
title: Avertissement du compilateur (niveau 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 2f457b5424cbca071e047f4375aaa85962e52210
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991485"
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
