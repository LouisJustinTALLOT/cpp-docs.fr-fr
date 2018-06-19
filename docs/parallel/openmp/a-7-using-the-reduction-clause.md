---
title: A.7 à l’aide de la réduction de la Clause | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e71e65bc-a25c-4f02-b507-66b52bf950a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfa7042d32ed3a82dc2cf73ab565f0db6b98d3d8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695247"
---
# <a name="a7---using-the-reduction-clause"></a>A.7   Utilisation de la clause reduction
L’exemple suivant illustre la clause reduction ([Section 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) à la page 28) :  
  
```  
#pragma omp parallel for private(i) shared(x, y, n) \  
                         reduction(+: a, b)  
    for (i=0; i<n; i++) {  
        a = a + x[i];  
        b = b + y[i];  
    }  
```