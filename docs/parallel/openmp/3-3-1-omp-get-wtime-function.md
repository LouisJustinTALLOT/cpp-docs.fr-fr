---
title: 3.3.1 Fonction omp_get_wtime
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460565"
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