---
title: Structures de données de synchronisation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f64acda5fe11cae3a40e4affc403ebb61d876de
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693804"
---
# <a name="synchronization-data-structures"></a>Structures de données de synchronisation
Le Runtime d’accès concurrentiel fournit plusieurs structures de données qui vous permettent de synchroniser l’accès aux données partagées à partir de plusieurs threads. Ces structures de données sont utiles lorsque vous avez partagé des données que vous modifiez rarement. Un objet de synchronisation, par exemple, une section critique, entraîne des autres threads d’attendre que la ressource partagée est disponible. Par conséquent, si vous utilisez un tel objet pour synchroniser l’accès aux données qui sont fréquemment utilisés, vous pouvez perdre l’extensibilité dans votre application. Le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) fournit le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) (classe), ce qui vous permet de partager une ressource entre plusieurs threads ou tâches sans avoir besoin pour la synchronisation. Pour plus d’informations sur la `combinable` de classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="top"></a> Sections  
 Cette rubrique décrit les types de blocs de messages asynchrones suivants en détail :  
  
-   [critical_section](#critical_section)  
  
-   [reader_writer_lock](#reader_writer_lock)  
  
-   [scoped_lock et scoped_lock_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a> critical_section  
 Le [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) classe représente un objet d’exclusion mutuelle coopératif qui cède à d’autres tâches au lieu d’anticiper les. Les sections critiques sont utiles lorsque plusieurs threads requièrent exclusif accès en lecture et écriture aux données partagées.  

 La `critical_section` classe est non réentrante. Le [Concurrency::critical_section :: lock](reference/critical-section-class.md#lock) méthode lève une exception de type [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) si elle est appelée par le thread qui détient déjà le verrou.  


  
### <a name="methods-and-features"></a>Méthodes et fonctionnalités  
 Le tableau suivant présente les méthodes importantes sont définis par le `critical_section` classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|Acquiert la section critique. Le contexte appelant bloque jusqu'à ce qu’il acquiert le verrou.|  
|[try_lock](reference/critical-section-class.md#try_lock)|Essaie d’acquérir la section critique, mais ne bloque pas.|  
|[unlock](reference/critical-section-class.md#unlock)|Libère la section critique.|  
  
 [[Haut](#top)]  
  
##  <a name="reader_writer_lock"></a> reader_writer_lock  
 Le [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) classe fournit des opérations thread-safe en lecture/écriture aux données partagées. Utiliser des verrous de lecteur/writer lorsque plusieurs threads requièrent un accès en lecture simultané à une ressource partagée mais écrivent rarement dans cette ressource partagée. Cette classe fournit un accès en écriture qu’un seul thread à un objet à tout moment.  
  
 Le `reader_writer_lock` classe peut effectuer plus performants que les `critical_section` classe car un `critical_section` objet acquiert un accès exclusif à une ressource partagée, ce qui empêche l’accès en lecture simultané.  
  
 Comme le `critical_section` (classe), la `reader_writer_lock` classe représente un objet d’exclusion mutuelle coopératif qui cède à d’autres tâches au lieu d’anticiper les.  
  
 Lorsqu’un thread doit écrire dans une ressource partagée acquiert un verrou de lecture/écriture, les autres threads qui doivent également accéder à la ressource sont bloqués jusqu'à ce que le writer libère le verrou. Le `reader_writer_lock` classe est un exemple d’un *préférence d’écriture* verrou, ce qui est un verrou qui débloque les writers en attente avant de débloquer les lecteurs en attente.  
  
 Comme le `critical_section` (classe), la `reader_writer_lock` classe est non réentrante. Le [concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) et [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) méthodes lèvent une exception de type `improper_lock` si elles sont appelées par un thread qui détient déjà le verrou.  


  
> [!NOTE]
>  Étant donné que la `reader_writer_lock` classe non réentrant, vous ne peut pas mettre à niveau un verrou en lecture seule à un verrou de lecture/écriture ou de la rétrogradation d’un verrou de lecture/écriture à un verrou en lecture seule. L’exécution d’une de ces opérations produit un comportement non spécifié.  
  
### <a name="methods-and-features"></a>Méthodes et fonctionnalités  
 Le tableau suivant présente les méthodes importantes sont définis par le `reader_writer_lock` classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|Acquiert l’accès en lecture/écriture au verrou.|  
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Essaie d’acquérir un accès en lecture/écriture au verrou, mais ne bloque pas.|  
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Acquiert un accès en lecture seule au verrou.|  
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Essaie d’acquérir un accès en lecture seule au verrou, mais ne bloque pas.|  
|[unlock](reference/reader-writer-lock-class.md#unlock)|Libère le verrou.|  
  
 [[Haut](#top)]  
  
##  <a name="scoped_lock"></a> scoped_lock et scoped_lock_read  
 Le `critical_section` et `reader_writer_lock` classes fournissent des classes d’assistance imbriquées qui simplifient la façon dont vous travaillez avec des objets d’exclusion mutuelle. Ces classes d’assistance sont appelés *verrous à portée limitée*.  
  
 Le `critical_section` classe contient le [Concurrency::critical_section :: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) classe. Le constructeur acquiert l’accès à la collection `critical_section` objet ; l’accès de versions de destructeur à cet objet. Le `reader_writer_lock` classe contient le [Concurrency::reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) (classe), qui ressemble à `critical_section::scoped_lock`, sauf qu’il gère l’accès en écriture à la collection `reader_writer_lock` objet. Le `reader_writer_lock` classe contient également le [Concurrency::reader_writer_lock :: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) classe. Cette classe gère l’accès en lecture à la collection `reader_writer_lock` objet.  

  
 Verrous à portée limitée offrent plusieurs avantages lorsque vous travaillez avec `critical_section` et `reader_writer_lock` objets manuellement. En règle générale, vous allouez un verrou à portée limitée sur la pile. Un verrou à portée limitée libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit ; Par conséquent, vous ne déverrouillez pas manuellement l’objet sous-jacent. Cela est utile lorsqu’une fonction contient plusieurs `return` instructions. Verrous à portée limitée peuvent également vous aider à écrire du code sécurisé à l’exception. Lorsqu’un `throw` instruction provoque le déroulement de pile, le destructeur de tout verrou à portée limitée actif est appelé, et par conséquent, l’objet de l’exclusion mutuelle est toujours correctement libéré.  
  
> [!NOTE]
>  Lorsque vous utilisez la `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, et `reader_writer_lock::scoped_lock_read` classes, ne libérez pas manuellement l’accès à l’objet d’exclusion mutuelle sous-jacent. Cela peut mettre le runtime dans un état non valide.  
  
##  <a name="event"></a> Événement  
 Le [concurrency::event](../../parallel/concrt/reference/event-class.md) classe représente un objet de synchronisation dont l’état peut être signalé ou non signalé. Contrairement aux objets de synchronisation, tels que les sections critiques, dont le but est de protéger l’accès aux données partagées, les événements synchronisent le flux d’exécution.  
  
 La `event` classe est utile lorsqu’une tâche a terminé le travail d’une autre tâche. Par exemple, une tâche peut signaler une autre tâche qu’il a lu les données à partir d’une connexion réseau ou d’un fichier.  
  
### <a name="methods-and-features"></a>Méthodes et fonctionnalités  
 Le tableau suivant répertorie plusieurs des méthodes importantes définies par la `event` classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|[attente](reference/event-class.md#wait)|Attend que l’événement soit signalé.|  
|[set](reference/event-class.md#set)|Définit l’événement à l’état signalé.|  
|[reset](reference/event-class.md#reset)|Définit l’événement à l’état non signalé.|  
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Attend que plusieurs événements soient signalés.|  

  
### <a name="example"></a>Exemple  
 Pour obtenir un exemple qui montre comment utiliser le `event` de classe, consultez [comparaison des Structures de données de synchronisation de l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Haut](#top)]  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 Compare le comportement des structures de données de synchronisation à ceux fournis par l’API Windows.  
  
 [Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)  
 Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.

