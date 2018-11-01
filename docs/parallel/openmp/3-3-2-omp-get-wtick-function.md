---
title: 3.3.2 Fonction omp_get_wtick
ms.date: 11/04/2016
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
ms.openlocfilehash: af1e5cf8ef40621342a5162f90cf8c883a59c6a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617956"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 Fonction omp_get_wtick

Le `omp_get_wtick` fonction retourne une valeur à virgule flottante double précision égale au nombre de secondes entre les battements d’horloge successives. Le format est le suivant :

```
#include <omp.h>
double omp_get_wtick(void);
```