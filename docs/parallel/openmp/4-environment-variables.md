---
title: 4. Variables d’environnement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690999"
---
# <a name="4-environment-variables"></a>4. Environment Variables
Ce chapitre décrit les variables d’environnement OpenMP C et C++ API (ou les mécanismes spécifiques à une plateforme équivalentes) qui contrôle l’exécution du code parallèle.  Les noms des variables d’environnement doivent être en majuscules. Les valeurs assignées à leur casse et peuvent avoir des espaces de début et de fin.  Modifications aux valeurs une fois que le programme a commencé sont ignorées.  
  
 Les variables d’environnement sont les suivantes :  
  
-   **OMP_SCHEDULE** définit la taille de segment et de type de planification de l’exécution.  
  
-   **OMP_NUM_THREADS** définit le nombre de threads à utiliser lors de l’exécution.  
  
-   **OMP_DYNAMIC** Active ou désactive l’ajustement dynamique du nombre de threads.  
  
-   **OMP_NESTED** Active ou désactive le parallélisme imbriqué.  
  
 Les exemples de ce chapitre montrent uniquement comment ces variables peuvent être définies dans les environnements Unix C shell (csh). Dans Korn shell et environnements de déni de service les actions sont similaires, comme suit :  
  
 csh :  
 setenv OMP_SCHEDULE « dynamique »  
  
 ksh :  
 Exporter OMP_SCHEDULE = « dynamiques »  
  
 DÉNI DE SERVICE :  
 définir OMP_SCHEDULE = « dynamiques »