---
title: 3.1.10 fonction omp_get_nested | Documents Microsoft
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
ms.openlocfilehash: 7f447da6957cb385ace918120eb7ed7a5420e9f0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686719"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Fonction omp_get_nested
Le `omp_get_nested` fonction retourne une valeur différente de zéro si le parallélisme imbriquée est activée et la valeur 0 si elle est désactivée. Pour plus d’informations sur le parallélisme imbriquée, consultez la Section 3.1.9 page 40. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Si une implémentation n’implémente pas le parallélisme imbriqué, cette fonction retourne toujours 0.