---
title: A.20   Liaison de directives barrier
ms.date: 11/04/2016
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
ms.openlocfilehash: cf6f20a8539c47ca529af93e65f3a5fe244228d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652944"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   Liaison de directives barrier

La liaison de directives règles d’appel pour un **barrière** directive à lier à la forme plus proche `parallel` directive. Pour plus d’informations sur la liaison de directives, consultez [Section 2.8](../../parallel/openmp/2-8-directive-binding.md) à la page 32.

Dans l’exemple suivant, l’appel de *principal* à *sub2* est conforme, car le **barrière** (dans *sub3*) est lié à la région parallèle dans *sub2*. L’appel de *principal* à *sub1* est conforme, car le **barrière** lie à la région parallèle de la sous-routine *sub2*.  L’appel de *principal* à *sub3* est conforme, car le **barrière** ne lie pas à n’importe quelle région parallèle et est ignoré. Notez également que le **barrière** synchronise uniquement l’équipe de threads dans la région parallèle englobante et pas tous les threads créés dans *sub1*.

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```