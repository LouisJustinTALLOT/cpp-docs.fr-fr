---
title: A.26 à l’aide de la Directive threadprivate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6eda76c2-c4f1-4208-a900-e0ea98a53eca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b74325ec96702838aaaf9be62d398178c8c2902
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690528"
---
# <a name="a26---using-the-threadprivate-directive"></a>A.26   Utilisation de la directive threadprivate
Les exemples suivants montrent comment utiliser le `threadprivate` directive ([Section 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) à la page 23) pour donner à chaque thread d’un compteur distinct.  
  
 **Exemple 1 :**  
  
```  
int counter = 0;  
#pragma omp threadprivate(counter)  
  
int sub()  
{  
    counter++;  
    return(counter);  
}  
```  
  
 **Exemple 2 :**  
  
```  
int sub()  
{  
    static int counter = 0;  
    #pragma omp threadprivate(counter)  
    counter++;  
    return(counter);  
}  
```