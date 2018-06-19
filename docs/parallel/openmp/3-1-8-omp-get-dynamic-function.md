---
title: 3.1.8 fonction omp_get_dynamic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af7755173ab884a40a5f8a41f432f265cc1e6c32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686189"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 Fonction omp_get_dynamic
Le **omp_get_dynamic** fonction retourne une valeur différente de zéro si l’ajustement dynamique de threads est activé, sinon, retourne 0. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 Si l’implémentation n’implémente pas l’ajustement dynamique du nombre de threads, cette fonction retourne toujours 0.  
  
## <a name="cross-references"></a>Références externes :  
  
-   Pour obtenir une description de l’ajustement de thread dynamique, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.