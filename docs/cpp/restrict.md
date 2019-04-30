---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403371"
---
# <a name="restrict"></a>restrict

**Section spécifique à Microsoft**

Lorsqu’il est appliqué à une déclaration de fonction ou d’une définition qui retourne un type pointeur, **restreindre** indique au compilateur que la fonction retourne un objet qui n’est pas *alias*, autrement dit, référencé par un autre pointeurs. Cela permet au compilateur d’effectuer des optimisations supplémentaires.

## <a name="syntax"></a>Syntaxe

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Notes

Le compilateur propage **__declspec (Restrict)**. Par exemple, la bibliothèque CRT `malloc` fonction a un **__declspec (Restrict)** décoration et par conséquent, le compilateur suppose que les pointeurs initialisés à des emplacements de mémoire par `malloc` ne sont pas un alias par précédemment pointeurs existants.

Le compilateur ne vérifie pas que le pointeur retourné n’est pas réellement un alias. Il est la responsabilité du développeur pour garantir le programme n’attribue pas d’alias à un pointeur marqué avec le **restreindre __declspec** modificateur.

Pour une sémantique similaire sur les variables, consultez [__restrict](../cpp/extension-restrict.md).

Pour une autre annotation s’applique aux alias dans une fonction, consultez [__declspec (noalias)](../cpp/noalias.md).

Pour plus d’informations sur la **restreindre** mot clé qui fait partie de C++ AMP, consultez [restreindre (C++ AMP)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de **__declspec (Restrict)**.

Lorsque **__declspec (Restrict)** est appliqué à une fonction que retourne un pointeur, cela indique au compilateur que la mémoire vers laquelle pointée la valeur de retour n’est pas un alias. Dans cet exemple, les pointeurs `mempool` et `memptr` sont globales, le compilateur ne peut pas être sûr que la mémoire, elles font référence à n’est pas un alias. Toutefois, elles sont utilisées dans `ma` et son appelant `init` d’une manière qui retourne la mémoire qui n’est pas référencé dans le cas contraire par le programme, par conséquent, **__decslpec(restrict)** est utilisé pour aider l’optimiseur. Ceci est similaire à la façon dont les en-têtes CRT décorent les fonctions d’allocation comme `malloc` à l’aide de **__declspec (Restrict)** pour indiquer qu’elles retournent toujours de mémoire qui ne peut pas être un alias en pointeurs existants.

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
