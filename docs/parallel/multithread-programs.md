---
title: Programmes multithread | Documents Microsoft
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
ms.openlocfilehash: ece834bd6bf85daacbbaf50110e6e278da1ae099
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686930"
---
# <a name="multithread-programs"></a>Programmes multithread
Un thread est un chemin d’accès de l’exécution via un programme. Il est également la plus petite unité d’exécution planifiée par Win32. Un thread se compose d’une pile, l’état des registres du processeur et une entrée dans la liste d’exécution du planificateur système. Chaque thread partage toutes les ressources du processus.  
  
 Un processus se compose d’un ou plusieurs threads et le code, données et autres ressources d’un programme en mémoire. Ressources programme standard sont des fichiers ouverts, les sémaphores et la mémoire allouée dynamiquement. Un programme s’exécute lorsque le planificateur du système donne une de ses threads de contrôle de l’exécution. Le planificateur détermine quels threads doivent s’exécuter et quand il doit s’exécuter. Threads de priorité inférieure peut-être patienter pendant que les threads de priorité plus élevées effectuer leurs tâches. Sur les ordinateurs multiprocesseurs, le planificateur peut répartir les threads entre les différents processeurs pour équilibrer la charge de l’UC.  
  
 Chaque thread dans un processus fonctionne de manière indépendante. À moins que les rendre visibles les uns aux autres, les threads s’exécutent individuellement et ne seront pas informés des autres threads dans un processus. Threads de partager des ressources communes, toutefois, doivent coordonner leur travail en utilisant des sémaphores ou une autre méthode de communication entre processus. Pour plus d’informations sur la synchronisation des threads, consultez [l’écriture d’un programme Win32 multithread](../parallel/writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)