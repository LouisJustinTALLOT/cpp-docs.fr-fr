---
title: Erreur du compilateur C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: f3650d994e3102f71ab1d3598a4d1482f50b3334
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510037"
---
# <a name="compiler-error-c3899"></a>Erreur du compilateur C3899

'var' : l’utilisation de l-value des données membres initonly n’est pas autorisée directement dans une région parallèle de la classe’class'

Une donnée membre [initonly (C++/CLI)](../../dotnet/initonly-cpp-cli.md) ne peut pas être initialisée dans cette partie d’un constructeur qui se trouve dans une région [parallèle](../../parallel/openmp/reference/openmp-directives.md#parallel) .  Cela est dû au fait que le compilateur effectue un déplacement interne de ce code, de telle sorte qu’il ne fait plus partie du constructeur.

Pour résoudre le, initialisez le membre de données initonly dans le constructeur, mais en dehors de la région parallèle.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3899.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
