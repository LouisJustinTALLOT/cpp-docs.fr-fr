---
title: Programmes multithread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25debffcd667c7e0d7405d0a4454b60729825fcb
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131279"
---
# <a name="multithread-programs"></a>Programmes multithread
Un thread est en fait un chemin d’exécution via un programme. Il est également la plus petite unité d’exécution planifiée par Win32. Un thread se compose d’une pile, l’état des registres du processeur et une entrée dans la liste de l’exécution du planificateur système. Chaque thread partage toutes les ressources du processus.  
  
Un processus se compose d’un ou plusieurs threads et le code, données et autres ressources d’un programme en mémoire. Ressources du programme classique sont des fichiers ouverts, les sémaphores et la mémoire allouée dynamiquement. Un programme s’exécute lorsque le planificateur système transmet un de ses threads contrôle d’exécution. Le planificateur détermine les threads qui doivent s’exécuter et quand il doit s’exécuter. Threads de priorité inférieure peuvent devoir patienter pendant que les threads de priorité plus élevées effectuer leurs tâches. Sur les ordinateurs multiprocesseurs, le planificateur peut déplacer des threads individuels à différents processeurs pour équilibrer la charge du processeur.  
  
Chaque thread dans un processus fonctionne de manière indépendante. Sauf si vous les rendre visibles entre eux, les threads s’exécutent individuellement et ne connaissent pas les autres threads dans un processus. Threads de partager des ressources communes, toutefois, doivent coordonner leur travail à l’aide des sémaphores ou une autre méthode de communication interprocessus. Pour plus d’informations sur la synchronisation des threads, consultez [écrire un programme Win32 multithread](writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Voir aussi  

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)