---
title: 4. Variables d’environnement | Microsoft Docs
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
ms.openlocfilehash: aec56dad334dcd27de2068e660ff8ec5a6e72f90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415488"
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