---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4835'
title: Avertissement du compilateur (niveau 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: ee5d91883bafcac3412962f7e314f2ee00ea8278
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197983"
---
# <a name="compiler-warning-level-1-c4835"></a>Avertissement du compilateur (niveau 1) C4835

'variable' : l’initialiseur des données exportées ne sera pas exécuté tant que le code managé n’aura pas été exécuté pour la première fois dans l’assembly hôte

Lors de l’accès aux données entre les composants managés, il est recommandé de ne pas utiliser les mécanismes d’importation et d’exportation C++ natifs. Au lieu de cela, déclarez vos données membres à l’intérieur d’un type managé et référencez les métadonnées avec `#using` dans le client. Pour plus d’informations, consultez [#using, directive](../../preprocessor/hash-using-directive-cpp.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4835.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

L’exemple suivant utilise le composant généré dans l’exemple précédent, indiquant que la valeur des variables n’est pas comme prévu.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
