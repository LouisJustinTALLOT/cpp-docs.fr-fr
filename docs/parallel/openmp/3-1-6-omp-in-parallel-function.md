---
title: 3.1.6 fonction omp_in_parallel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404616"
---
# <a name="316-ompinparallel-function"></a>3.1.6 Fonction omp_in_parallel

Le **omp_in_parallel** fonction retourne une valeur différente de zéro si elle est appelée dans l’étendue dynamique d’une région parallèle s’exécutaient en parallèle ; sinon, elle retourne 0. Le format est le suivant :

```
#include <omp.h>
int omp_in_parallel(void);
```

Cette fonction retourne une valeur différente de zéro lorsque appelé à partir d’une région s’exécutant en parallèle, y compris des zones imbriquées qui sont sérialisés.