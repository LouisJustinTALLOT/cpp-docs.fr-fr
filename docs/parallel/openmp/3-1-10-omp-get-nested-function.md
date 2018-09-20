---
title: 3.1.10 fonction omp_get_nested | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392279"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Fonction omp_get_nested

Le `omp_get_nested` fonction retourne une valeur différente de zéro si le parallélisme imbriquée est activée et 0 s’il est désactivé. Pour plus d’informations sur le parallélisme imbriquée, consultez Section 3.1.9 sur la page 40. Le format est le suivant :

```
#include <omp.h>
int omp_get_nested(void);
```

Si une implémentation n’implémente pas le parallélisme imbriqué, cette fonction retourne toujours 0.