---
title: Avertissement du compilateur (niveau 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: 0427a97a9e368a19a40a8d1a552f7713e36f831e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516309"
---
# <a name="compiler-warning-level-1-c4835"></a>Avertissement du compilateur (niveau 1) C4835

'variable' : l’initialiseur des données exportées ne sera pas exécuté jusqu'à ce que le code managé pour la première fois dans l’assembly hôte

Lors de l’accès aux données entre les composants managés, il est recommandé de pas utiliser native C++ importer et exporter des mécanismes. Au lieu de cela, déclarez vos membres de données à l’intérieur d’un type managé et référencez les métadonnées avec `#using` dans le client. Pour plus d’informations, consultez [#using, directive](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4835.

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Exemple

L’exemple suivant utilise le composant généré dans l’exemple précédent, indiquant que la valeur des variables est ne pas comme prévu.

```
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