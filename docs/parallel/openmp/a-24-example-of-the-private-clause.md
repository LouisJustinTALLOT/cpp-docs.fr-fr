---
title: A.24 exemple de la Clause private | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df2efc9fe111fa6e8d0b0507eceb20f07f48b02d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416238"
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