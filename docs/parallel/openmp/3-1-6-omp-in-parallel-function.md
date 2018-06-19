---
title: 3.1.6 fonction omp_in_parallel | Documents Microsoft
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
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686280"
---
# <a name="316-ompinparallel-function"></a>3.1.6 Fonction omp_in_parallel
Le **omp_in_parallel** fonction retourne une valeur différente de zéro si elle est appelée dans l’étendue dynamique d’une région parallèle s’exécutant en parallèle ; sinon, retourne 0. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Cette fonction retourne une valeur différente de zéro lors de l’appelé à partir d’une région s’exécutant en parallèle, notamment des zones imbriquées qui sont sérialisés.