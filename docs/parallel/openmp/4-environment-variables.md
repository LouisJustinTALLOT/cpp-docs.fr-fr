---
title: 4. Environment Variables
ms.date: 11/04/2016
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 0dec302762ad22fc3c7f6691ef63df1b07d5940d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456600"
---
# <a name="4-environment-variables"></a>4. Environment Variables

Ce chapitre décrit les variables d’environnement OpenMP C et C++ API (ou équivalents mécanismes spécifiques à la plateforme) qui contrôlent l’exécution du code parallèle.  Les noms des variables d’environnement doivent être en majuscules. Les valeurs affectées à leur respectent la casse et peuvent avoir des espaces de début et de fin.  Modifications aux valeurs une fois que le programme a commencé sont ignorées.

Les variables d’environnement sont les suivantes :

- **OMP_SCHEDULE** définit la taille de segment et de type de planification de l’exécution.

- **OMP_NUM_THREADS** définit le nombre de threads à utiliser lors de l’exécution.

- **OMP_DYNAMIC** Active ou désactive l’ajustement dynamique du nombre de threads.

- **OMP_NESTED** Active ou désactive le parallélisme imbriqué.

Les exemples dans ce chapitre montrent uniquement comment ces variables peuvent être définies dans les environnements Unix C shell (csh). Dans Korn shell et environnements DOS les actions sont similaires, comme suit :

csh : setenv OMP_SCHEDULE « dynamic »

ksh : exporter OMP_SCHEDULE = « dynamique »

DOS : définissez OMP_SCHEDULE = « dynamique »