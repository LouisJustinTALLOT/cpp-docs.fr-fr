---
title: 3. Fonctions de bibliothèque du Run-time
ms.date: 11/04/2016
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: e1d8d498be7f58bcf510025c67c539127f450824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484095"
---
# <a name="3-run-time-library-functions"></a>3. Fonctions de bibliothèque du Run-time

Cette section décrit les fonctions de bibliothèque du run-time OpenMP C et C++. L’en-tête  **\<omp.h >** déclare deux types, plusieurs fonctions qui peuvent être utilisées pour contrôler et interroger l’environnement d’exécution en parallèle et verrouiller les fonctions qui peuvent être utilisées pour synchroniser l’accès aux données.

Le type **omp_lock_t** est un type d’objet capable de représenter qu’un verrou est disponible, ou qu’un thread possède un verrou. Ces verrous sont appelés *verrous simples*.

Le type **imbriqué omp_nest_lock_t** est un type d’objet capable de représenter qu’un verrou est disponible, ou l’identité du thread qui détient le verrou et un *imbrication nombre* (décrits ci-dessous). Ces verrous sont appelés *verrous pouvant être imbriqués*.

Les fonctions de bibliothèque sont des fonctions externes avec une liaison de « C ».

Les descriptions dans ce chapitre sont réparties dans les rubriques suivantes :

- Fonctions de l’environnement d’exécution (consultez [Section 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) sur la page 35).

- Fonctions de verrouillage (consultez [Section 3.2](../../parallel/openmp/3-2-lock-functions.md) page 41).