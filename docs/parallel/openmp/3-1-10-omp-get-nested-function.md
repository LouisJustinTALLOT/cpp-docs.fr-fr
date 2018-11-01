---
title: 3.1.10 Fonction omp_get_nested
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519918"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Fonction omp_get_nested

Le `omp_get_nested` fonction retourne une valeur différente de zéro si le parallélisme imbriquée est activée et 0 s’il est désactivé. Pour plus d’informations sur le parallélisme imbriquée, consultez Section 3.1.9 sur la page 40. Le format est le suivant :

```
#include <omp.h>
int omp_get_nested(void);
```

Si une implémentation n’implémente pas le parallélisme imbriqué, cette fonction retourne toujours 0.