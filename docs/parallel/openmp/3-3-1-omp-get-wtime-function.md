---
title: 3.3.1 fonction omp_get_wtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec022e9c7e27c848ef535481993dd18dc45f695
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430765"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 Fonction omp_get_wtime

Le `omp_get_wtime` fonction retourne une valeur à virgule flottante double précision égale à la durée totale écoulée en secondes depuis « ultérieurement dans le passé ».  L’heure « réelle dans le passé » est arbitraire, mais il ne peut ne pas changer pendant l’exécution du programme d’application. Le format est le suivant :

```
#include <omp.h>
double omp_get_wtime(void);
```

Il est prévu que la fonction sera être utilisée pour mesurer le temps écoulé comme indiqué dans l’exemple suivant :

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Les heures retournées sont « fois par thread » en ce qui est signifiait que pas devoir être globalement cohérente sur tous les threads qui participent à une application.