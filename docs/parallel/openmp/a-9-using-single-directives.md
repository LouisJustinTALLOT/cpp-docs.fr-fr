---
title: A.9 Utilisation de Directives simples | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3a201450d54355aa96f0ea712ad9fa0f70f63f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448088"
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