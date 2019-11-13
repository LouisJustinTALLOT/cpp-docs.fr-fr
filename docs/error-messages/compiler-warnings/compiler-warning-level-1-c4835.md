---
title: Avertissement du compilateur (niveau 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: e59c8a7c9cdd9b892155a7d8ee8c8259324c2045
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052305"
---
# <a name="compiler-warning-level-1-c4835"></a>Avertissement du compilateur (niveau 1) C4835

'variable' : l’initialiseur des données exportées ne sera pas exécuté tant que le code managé n’aura pas été exécuté pour la première fois dans l’assembly hôte

Lors de l’accès aux données entre les composants managés, il est recommandé de C++ ne pas utiliser les mécanismes d’importation et d’exportation natifs. Au lieu de cela, déclarez vos données membres à l’intérieur d’un type managé et référencez les métadonnées avec `#using` dans le client. Pour plus d’informations, consultez [#using, directive](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4835.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Exemple

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