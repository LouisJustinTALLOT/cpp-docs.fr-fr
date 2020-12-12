---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4005'
title: Avertissement du compilateur (niveau 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: a8de4974d87eb5d8396085bb79dfbfe14a177602
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325985"
---
# <a name="compiler-warning-level-1-c4005"></a>Avertissement du compilateur (niveau 1) C4005

'identificateur' : redéfinition de macro

L’identificateur de macro est défini deux fois. Le compilateur utilise la deuxième définition de macro.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Définition d’une macro sur la ligne de commande et dans le code à l’aide d’une `#define` directive.

1. Macros importées à partir de fichiers include.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Supprimez l’une des définitions.

1. Utilisez une directive [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) avant la deuxième définition.

L’exemple suivant génère l’C4005 :

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```
