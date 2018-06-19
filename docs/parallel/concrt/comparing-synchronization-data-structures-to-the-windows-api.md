---
title: Comparaison des Structures de données de synchronisation avec l’API Windows | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d1470911b13243a7c8b3befc627801368e89f04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687372"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Comparaison des structures de données de synchronisation avec l’API Windows
Cette rubrique compare le comportement des structures de données de synchronisation fournies par le Runtime d’accès concurrentiel à ceux fournis par l’API Windows.  
  
 Les structures de données de synchronisation fournies par le Runtime d’accès concurrentiel suivent le *coopératif de modèle de thread*. Dans le modèle de thread coopératif, les primitives de synchronisation soumis explicitement leurs ressources de traitement à d’autres threads. Cela diffère de la *préemptif, modèle de thread*, où les ressources de traitement sont transférées à d’autres threads par le Planificateur de contrôle ou d’un système d’exploitation.  
  
## <a name="criticalsection"></a>critical_section  
 Le [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) ressemble à Windows `CRITICAL_SECTION` car il peut être utilisé uniquement par les threads d’un processus de la structure. Pour plus d’informations sur les sections critiques dans l’API Windows, consultez [objets de Section critique](http://msdn.microsoft.com/library/windows/desktop/ms682530).  
  
## <a name="readerwriterlock"></a>reader_writer_lock  
 Le [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) classe ressemble à des verrous de lecteur/writer compacte (SRW) de Windows. Le tableau suivant explique les similitudes et les différences.  
  
|Fonctionnalité|`reader_writer_lock`|Verrou SRW|  
|-------------|--------------------------|--------------|  
|Non réentrant|Oui|Oui|  
|Peut promouvoir un lecteur à un writer (mise à niveau prise en charge)|Non|Non|  
|Peut rétrograder un enregistreur à un lecteur (prise en charge de la rétrogradation)|Non|Non|  
|Verrou de préférence d’écriture|Oui|Non|  
|Accès FIFO aux enregistreurs|Oui|Non|  
  
 Pour plus d’informations sur les verrous SRW, consultez [des verrous de lecture/écriture compacte (SRW)](http://msdn.microsoft.com/library/windows/desktop/aa904937) dans le Kit de développement de plate-forme.  
  
## <a name="event"></a>événement  
 Le [concurrency::event](../../parallel/concrt/reference/event-class.md) ressemble à un événement de réinitialisation manuelle de Windows sans nom. Toutefois, un `event` objet se comporte de manière coopérative, alors qu’un événement Windows se comporte de manière préemptive. Pour plus d’informations sur les événements Windows, consultez [objets événement](http://msdn.microsoft.com/library/windows/desktop/ms682655).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Pour mieux comprendre la différence entre la `event` classe et des événements Windows, considérez l’exemple suivant. Cet exemple active le Planificateur de créer au plus deux tâches simultanées, puis appelle similaire deux fonctions qui utilisent la `event` classe et un événement de réinitialisation manuelle de Windows. Chaque fonction crée d’abord plusieurs tâches qui attendent qu’un événement partagé soit signalé. Chaque fonction produit ensuite aux tâches en cours d’exécution et signale l’événement. Chaque fonction attend ensuite l’événement signalé.  
  
### <a name="code"></a>Code  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère la sortie suivante :  
  
```Output  
Cooperative event:  
    Context 0: waiting on an event.  
    Context 1: waiting on an event.  
    Context 2: waiting on an event.  
    Context 3: waiting on an event.  
    Context 4: waiting on an event.  
    Setting the event.  
    Context 5: received the event.  
    Context 6: received the event.  
    Context 7: received the event.  
    Context 8: received the event.  
    Context 9: received the event.  
Windows event:  
    Context 10: waiting on an event.  
    Context 11: waiting on an event.  
    Setting the event.  
    Context 12: received the event.  
    Context 14: waiting on an event.  
    Context 15: received the event.  
    Context 16: waiting on an event.  
    Context 17: received the event.  
    Context 18: waiting on an event.  
    Context 19: received the event.  
    Context 13: received the event.  
```  
  
 Étant donné que la `event` classe se comporte de manière coopérative, le planificateur peut réaffecter les ressources de traitement à un autre contexte lorsqu’un événement est en attente à l’état signalé. Par conséquent, davantage de travail est accompli par la version qui utilise le `event` classe. Dans la version qui utilise des événements Windows, chaque tâche en attente doive entrer l’état signalé avant le début de la tâche suivante.  
  
 Pour plus d’informations sur les tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)
