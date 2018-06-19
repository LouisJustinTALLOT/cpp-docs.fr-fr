---
title: Directives uniques à l’aide A.9 | Documents Microsoft
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
ms.openlocfilehash: bc0e0e08b0b7bdea05bf4c627ae33cc42298c6dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690379"
---
# <a name="a9---using-single-directives"></a>A.9   Utilisation de directives simples
L’exemple suivant illustre la `single` directive ([Section 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) page 15). Dans l’exemple, un seul thread (généralement le premier thread qui rencontre le `single` directive) imprime le message de progression. L’utilisateur ne doit pas faire d’hypothèses comme pour le thread s’exécute le `single` section. Tous les autres threads ignorera la `single` section et s’arrêter à la barrière à la fin de la `single` construire. Si les autres threads peuvent continuer sans attendre que le thread qui exécute le `single` section, un `nowait` clause peut être spécifiée sur le `single` la directive.  
  
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