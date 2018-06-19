---
title: 3. Fonctions de la bibliothèque Runtime | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688113"
---
# <a name="3-run-time-library-functions"></a>3. Fonctions de la bibliothèque Runtime
Cette section décrit les fonctions de bibliothèque OpenMP C et C++. L’en-tête  **\<omp.h >** déclare deux types, plusieurs fonctions qui peuvent être utilisées pour contrôler l’environnement d’exécution parallèle de la requête et verrouiller des fonctions qui peuvent être utilisées pour synchroniser l’accès aux données.  
  
 Le type **omp_lock_t** un type d’objet n’est capable de représenter qu’un verrou est disponible ou qu’un thread possède un verrou. Ces verrous sont appelés *verrous simples*.  
  
 Le type **omp_nest_lock_t** est un type d’objet capable de représenter qu’un verrou est disponible, ou l’identité du thread qui détient le verrou et un *imbrication nombre* (décrites ci-dessous). Ces verrous sont appelés *verrous pouvant*.  
  
 Les fonctions de bibliothèque sont des fonctions externes avec une liaison de « C ».  
  
 Les descriptions de ce chapitre sont réparties dans les rubriques suivantes :  
  
-   Fonctions de l’environnement d’exécution (consultez [Section 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) à la page 35).  
  
-   Fonctions de verrouillage (consultez [Section 3.2](../../parallel/openmp/3-2-lock-functions.md) page 41).