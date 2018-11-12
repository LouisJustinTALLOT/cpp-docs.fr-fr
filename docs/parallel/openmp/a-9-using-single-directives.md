---
title: A.9   Utilisation de directives simples
ms.date: 11/04/2016
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
ms.openlocfilehash: 51a2a3438ae5abc9d24c160a986c8ea04b77c4bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501307"
---
# <a name="a9---using-single-directives"></a>A.9   Utilisation de directives simples

L’exemple suivant montre le `single` directive ([Section 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) page 15). Dans l’exemple, un seul thread (généralement le premier thread qui rencontre le `single` directive) imprime le message de progression. L’utilisateur ne doit pas faire d’hypothèses comme pour le thread qui exécutera le `single` section. Tous les autres threads ignorera la `single` section et arrêter à la barrière à la fin de la `single` construire. Si les autres threads puissent poursuivre sans attendre que le thread s’exécutant le `single` section, un `nowait` clause peut être spécifiée sur la `single` directive.

```
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```