---
title: 3.3.1 fonction omp_get_wtime | Documents Microsoft
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
ms.openlocfilehash: d71296d23df72464ed730713566c95e2403760a1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689491"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 Fonction omp_get_wtime
Le `omp_get_wtime` fonction retourne une valeur à virgule flottante double précision égale à la durée écoulée totale d’exécution en secondes depuis le « moment donné dans le passé ».  L’heure « réelle dans le passé » est arbitraire, mais il ne peut ne pas changer pendant l’exécution de l’application. Le format est le suivant :  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 Il est prévu que la fonction servira pour mesurer le temps écoulé tel qu’indiqué dans l’exemple suivant :  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 Les temps retournés sont « délais par thread » par qui est destinée qu’ils ne doivent pas être globalement cohérente sur tous les threads qui participe à une application.