---
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 70c1f4e8bfa426e858014a78febc424b473a89ae
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127878"
---
# `noalias`

**Spécifique à Microsoft**

**`noalias`** signifie qu’un appel de fonction ne modifie pas ou ne référence pas l’état global visible et modifie uniquement la mémoire vers laquelle pointe *directement* les paramètres de pointeur (indirections de premier niveau).

Si une fonction est annotée comme **`noalias`** , l’optimiseur peut supposer que seuls les paramètres eux-mêmes et uniquement les indirections de premier niveau des paramètres de pointeur sont référencés ou modifiés à l’intérieur de la fonction.

L' **`noalias`** annotation s’applique uniquement dans le corps de la fonction annotée. Le marquage d’une fonction comme **`__declspec(noalias)`** n’affecte pas l’alias des pointeurs retournés par la fonction.

Pour obtenir une autre annotation qui peut avoir un impact sur les alias, consultez [`__declspec(restrict)`](../cpp/restrict.md) .

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de **`__declspec(noalias)`** .

Lorsque la fonction `multiply` qui accède à la mémoire est annotée **`__declspec(noalias)`** , elle indique au compilateur que cette fonction ne modifie pas l’état global, sauf par le biais des pointeurs figurant dans sa liste de paramètres.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
