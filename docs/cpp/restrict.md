---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: a0108cff3d6b98fd929b7888d2ad718e7b6b3a64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213253"
---
# <a name="restrict"></a>restrict

**Spécifique à Microsoft**

En cas d’application à une déclaration ou une définition de fonction qui retourne un type pointeur, **`restrict`** indique au compilateur que la fonction retourne un objet qui n’est pas un *alias*, autrement dit, référencé par tout autre pointeur. Cela permet au compilateur d’effectuer des optimisations supplémentaires.

## <a name="syntax"></a>Syntaxe

> **`__declspec(restrict)`***pointer_return_type* *fonction*();

## <a name="remarks"></a>Notes

Le compilateur se propage **`__declspec(restrict)`** . Par exemple, la `malloc` fonction CRT a une **`__declspec(restrict)`** décoration, et par conséquent, le compilateur suppose que les pointeurs initialisés aux emplacements de mémoire par `malloc` ne sont pas non plus des alias des pointeurs existants.

Le compilateur ne vérifie pas que le pointeur retourné n’est pas réellement un alias. Il incombe au développeur de s’assurer que le programme n’utilise pas l’alias d’un pointeur marqué avec le modificateur **restrict __declspec** .

Pour obtenir une sémantique similaire sur les variables, consultez [__restrict](../cpp/extension-restrict.md).

Pour obtenir une autre annotation qui s’applique aux alias dans une fonction, consultez [__declspec (noalias)](../cpp/noalias.md).

Pour plus d’informations sur le **`restrict`** mot clé qui fait partie de C++ amp, consultez [restrict (C++ amp)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de **`__declspec(restrict)`** .

Lorsque **`__declspec(restrict)`** est appliqué à une fonction qui retourne un pointeur, cela indique au compilateur que la mémoire vers laquelle pointe la valeur de retour n’est pas un alias. Dans cet exemple, les pointeurs `mempool` et `memptr` sont globaux, de sorte que le compilateur ne peut pas s’assurer que la mémoire à laquelle ils font référence n’est pas un alias. Toutefois, elles sont utilisées dans `ma` et son appelant `init` d’une manière qui retourne la mémoire qui n’est pas référencée par le programme, donc **__decslpec (restrict)** est utilisé pour aider l’optimiseur. Cela est similaire à la façon dont les en-têtes CRT décorent les fonctions d’allocation comme `malloc` en utilisant **`__declspec(restrict)`** pour indiquer qu’elles retournent toujours la mémoire qui ne peut pas être un alias par des pointeurs existants.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec (noalias)](../cpp/noalias.md)
