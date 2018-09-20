---
title: A.20 liaison de Directives barrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628920caa6a122230f42394cc757e3abdb1874cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381307"
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