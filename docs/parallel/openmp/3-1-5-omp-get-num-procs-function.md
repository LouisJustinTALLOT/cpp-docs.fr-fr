---
title: 3.1.5 fonction omp_get_num_procs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 692bf39ea6d67f3ef9b850ddba187bbde98cb64c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705313"
---
# <a name="315-ompgetnumprocs-function"></a>3.1.5 Fonction omp_get_num_procs
Le `omp_get_num_procs` fonction retourne le nombre de processeurs qui sont disponibles pour le programme au moment de la fonction est appelée. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_num_procs(void);  
```