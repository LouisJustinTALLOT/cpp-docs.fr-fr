---
title: A.8 spécifiant Sections parallèles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acb28f4e7e99ea09696d116ab031778fcf9ff919
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694054"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   Spécification des sections parallel
Dans l’exemple suivant, (pour [Section 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) page 14) fonctions *xaxis*, *yaxis*, et *zaxis* peuvent être exécutées simultanément. La première `section` la directive est facultative.  Notez que tous les `section` directives doivent apparaître dans l’étendue lexicale de la `parallel sections` construire.  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```