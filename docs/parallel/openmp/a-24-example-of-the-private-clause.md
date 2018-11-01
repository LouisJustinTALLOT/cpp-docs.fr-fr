---
title: A.24   Exemple de la clause private
ms.date: 11/04/2016
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
ms.openlocfilehash: facf5b953b26d284f6bfed4f35a9162f6d2bf212
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552956"
---
# <a name="a24---example-of-the-private-clause"></a>A.24   Exemple de la clause private

Le `private` clause ([Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25) d’une région parallèle n’est en vigueur pour l’étendue lexicale de la région, mais pas pour l’étendue dynamique de la région.  Par conséquent, dans l’exemple qui suit, toutes les utilisations de la variable *un* au sein de la `for` boucle dans la routine *f* fait référence à une copie privée de *un*, tandis que d’une utilisation dans routine *g* fait référence au modèle global *un*.

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```