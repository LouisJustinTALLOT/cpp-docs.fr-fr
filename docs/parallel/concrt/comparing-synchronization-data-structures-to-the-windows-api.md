---
title: Comparaison des structures de données de synchronisation avec l’API Windows
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510590"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Comparaison des structures de données de synchronisation avec l’API Windows

Cette rubrique compare le comportement des structures de données de synchronisation fournies par le runtime d’accès concurrentiel à celles fournies par l’API Windows.

Les structures de données de synchronisation fournies par le runtime d’accès concurrentiel suivre le *modèle de thread coopératif*. Dans le modèle de thread coopérative, les primitives de synchronisation produisent explicitement leurs ressources de traitement à d’autres threads. Cela diffère du *modèle de thread préemptif*, où les ressources de traitement sont transférées vers d’autres threads par le planificateur ou le système d’exploitation qui contrôle.

## <a name="critical_section"></a>critical_section

La classe [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) ressemble à la structure `CRITICAL_SECTION` Windows, car elle ne peut être utilisée que par les threads d’un processus. Pour plus d’informations sur les sections critiques de l’API Windows, consultez la [section objets de section critique](/windows/win32/Sync/critical-section-objects).

## <a name="reader_writer_lock"></a>reader_writer_lock

La classe [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) ressemble aux verrous SRW (Windows Slim Reader/Writer). Le tableau suivant explique les similitudes et les différences.

|Fonctionnalité|`reader_writer_lock`|Verrou SRW|
|-------------|--------------------------|--------------|
|Non réentrant|Oui|Oui|
|Peut promouvoir un lecteur en écriture (prise en charge de la mise à niveau)|Non|Non|
|Peut rétrograder un enregistreur à un lecteur (prise en charge de la rétrogradation)|Non|Non|
|Verrou de préférence en écriture|Oui|Non|
|Accès FIFO aux rédacteurs|Oui|Non|

Pour plus d’informations sur les verrous SRW, consultez [verrous SRW (Slim Reader/Writer)](/windows/win32/sync/slim-reader-writer--srw--locks) dans le kit de développement logiciel (SDK) de plateforme.

## <a name="event"></a>événement

La classe [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) ressemble à un événement sans nom de réinitialisation manuelle de Windows. Toutefois, un `event` objet se comporte de manière coopérative, tandis qu’un événement Windows se comporte de manière préemptive. Pour plus d’informations sur les événements Windows, consultez [objets d’événement](/windows/win32/Sync/event-objects).

## <a name="example"></a>Exemples

### <a name="description"></a>Description

Pour mieux comprendre la différence entre les `event` événements de classe et Windows, examinez l’exemple suivant. Cet exemple permet au planificateur de créer au maximum deux tâches simultanées, puis d’appeler deux fonctions similaires qui utilisent `event` la classe et un événement de réinitialisation manuelle de Windows. Chaque fonction crée d’abord plusieurs tâches qui attendent qu’un événement partagé soit signalé. Chaque fonction produit ensuite les tâches en cours d’exécution, puis signale l’événement. Chaque fonction attend ensuite l’événement signalé.

### <a name="code"></a>Code

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Commentaires

Cet exemple produit l’exemple de sortie suivant:

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

Étant donné `event` que la classe se comporte de manière coopérative, le planificateur peut réallouer les ressources de traitement à un autre contexte lorsqu’un événement attend pour passer à l’état signalé. Par conséquent, une plus grande charge de travail est effectuée par `event` la version qui utilise la classe. Dans la version qui utilise des événements Windows, chaque tâche en attente doit entrer dans l’état signalé avant le démarrage de la tâche suivante.

Pour plus d’informations sur les tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Voir aussi

[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)
