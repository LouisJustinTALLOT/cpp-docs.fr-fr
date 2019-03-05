---
title: Structures de données de synchronisation
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: f9b949e7782c4b9ca302e9e623ce5f09061c39ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301881"
---
# <a name="synchronization-data-structures"></a>Structures de données de synchronisation

Le Runtime d’accès concurrentiel fournit plusieurs structures de données qui vous permettent de synchroniser l’accès aux données partagées à partir de plusieurs threads. Ces structures de données sont utiles lorsque vous avez partagé des données que vous modifiez rarement. Un objet de synchronisation, par exemple, une section critique, provoque des autres threads à attendre jusqu'à ce que la ressource partagée est disponible. Par conséquent, si vous utilisez ce type d’objet pour synchroniser l’accès aux données qui sont fréquemment utilisées, vous pouvez perdre l’évolutivité dans votre application. Le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) fournit le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) (classe), qui vous permet de partager une ressource entre plusieurs threads ou tâches sans la nécessité de synchronisation. Pour plus d’informations sur la `combinable` de classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="top"></a> Sections

Cette rubrique décrit les types de blocs de messages asynchrones suivants en détail :

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock et scoped_lock_read](#scoped_lock)

- [event](#event)

##  <a name="critical_section"></a> critical_section

Le [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) classe représente un objet d’exclusion mutuelle coopératif qui cède à d’autres tâches au lieu de les préempter. Les sections critiques sont utiles lorsque plusieurs threads requièrent exclusif accès en lecture et écriture aux données partagées.

Le `critical_section` classe est non réentrante. Le [Concurrency::critical_section :: lock](reference/critical-section-class.md#lock) méthode lève une exception de type [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) si elle est appelée par le thread qui détient déjà le verrou.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente les méthodes importantes qui sont définies par le `critical_section` classe.

|Méthode|Description|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Acquiert la section critique. Le contexte appelant bloque jusqu'à ce qu’il acquiert le verrou.|
|[try_lock](reference/critical-section-class.md#try_lock)|Tente d’acquérir la section critique, mais ne bloque pas.|
|[unlock](reference/critical-section-class.md#unlock)|Libère la section critique.|

[[Haut](#top)]

##  <a name="reader_writer_lock"></a> reader_writer_lock

Le [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) classe fournit les opérations thread-safe en lecture/écriture aux données partagées. Utiliser des verrous de lecture/écriture lorsque plusieurs threads requièrent un accès en lecture simultané à une ressource partagée, mais rarement écrivent sur cette ressource partagée. Cette classe fournit un accès en écriture qu’un seul thread à un objet à tout moment.

Le `reader_writer_lock` classe peut effectuer mieux que le `critical_section` classe, car un `critical_section` objet acquiert l’accès exclusif à une ressource partagée, ce qui empêche l’accès en lecture simultané.

Comme le `critical_section` (classe), la `reader_writer_lock` classe représente un objet d’exclusion mutuelle coopératif qui cède à d’autres tâches au lieu de les préempter.

Lorsqu’un thread qui doit écrire dans une ressource partagée acquiert un verrou de lecture/écriture, les autres threads qui doivent également accéder à la ressource sont bloqués jusqu'à ce que le writer libère le verrou. Le `reader_writer_lock` classe est un exemple d’un *préférence d’écriture* verrou, ce qui est un verrou qui débloque les writers en attente avant de débloquer les lectures en attente.

Comme le `critical_section` (classe), la `reader_writer_lock` classe est non réentrante. Le [concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) et [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) méthodes lèvent une exception de type `improper_lock` si elles sont appelées par un thread qui détient déjà le verrou.

> [!NOTE]
>  Étant donné que la `reader_writer_lock` classe non réentrants, vous ne pouvez pas mettre à niveau un verrou en lecture seule à un verrou de lecture/écriture ou rétrograder un verrou en lecture/écriture à un verrou en lecture seule. Effectuez une de ces opérations provoque un comportement inattendu.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente les méthodes importantes qui sont définies par le `reader_writer_lock` classe.

|Méthode|Description|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Acquiert l’accès en lecture/écriture au verrou.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Tente d’acquérir l’accès en lecture/écriture au verrou, mais ne bloque pas.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Acquiert l’accès en lecture seule au verrou.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Tente d’acquérir un accès en lecture seule au verrou, mais ne bloque pas.|
|[unlock](reference/reader-writer-lock-class.md#unlock)|Libère le verrou.|

[[Haut](#top)]

##  <a name="scoped_lock"></a> scoped_lock et scoped_lock_read

Le `critical_section` et `reader_writer_lock` classes fournissent des classes d’assistance imbriquées qui simplifient la façon dont vous travaillez avec des objets d’exclusion mutuelle. Ces classes d’assistance sont appelées *verrous à portée limitée*.

Le `critical_section` classe contient le [Concurrency::critical_section :: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) classe. Le constructeur acquiert l’accès à la collection `critical_section` objet ; l’accès de versions de destructeur à cet objet. Le `reader_writer_lock` classe contient le [Concurrency::reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) (classe), qui ressemble à `critical_section::scoped_lock`, sauf qu’il gère l’accès en écriture à la collection `reader_writer_lock` objet. Le `reader_writer_lock` classe contient également le [Concurrency::reader_writer_lock :: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) classe. Cette classe gère l’accès en lecture à la collection `reader_writer_lock` objet.

Verrous à portée limitée procurent plusieurs avantages lorsque vous travaillez avec `critical_section` et `reader_writer_lock` objets manuellement. En règle générale, vous allouez un verrou à portée limitée sur la pile. Un verrou à portée limitée libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit ; Par conséquent, vous ne déverrouillez pas manuellement l’objet sous-jacent. Cela est utile lorsqu’une fonction contient plusieurs `return` instructions. Verrous à portée limitée peuvent également vous aider à écrire du code d’exception-safe. Quand un `throw` instruction provoque le déroulement de pile, le destructeur de tout verrou à portée limitée actif est appelé, et par conséquent l’objet d’exclusion mutuelle est toujours correctement diffusé.

> [!NOTE]
>  Lorsque vous utilisez le `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, et `reader_writer_lock::scoped_lock_read` classes, ne libèrent pas manuellement l’accès à l’objet d’exclusion mutuelle sous-jacent. Ceci peut mettre le runtime dans un état non valide.

##  <a name="event"></a> Événement

Le [concurrency::event](../../parallel/concrt/reference/event-class.md) classe représente un objet de synchronisation dont l’état peut être signalé ou non signalé. Contrairement aux objets de synchronisation, tels que les sections critiques, dont l’objectif est de protéger l’accès aux données partagées, événements de synchronisent les flux d’exécution.

Le `event` classe est utile lorsqu’une tâche a terminé le travail d’une autre tâche. Par exemple, une tâche peut signaler une autre tâche qu’il a lu les données à partir d’une connexion réseau ou d’un fichier.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente plusieurs méthodes importantes qui sont définies par le `event` classe.

|Méthode|Description|
|------------|-----------------|
|[wait](reference/event-class.md#wait)|Attend que l’événement soit signalé.|
|[set](reference/event-class.md#set)|Définit l’événement signalé.|
|[reset](reference/event-class.md#reset)|Définit l’événement à l’état non signalé.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Attend que plusieurs événements soit signalé.|

### <a name="example"></a>Exemple

Pour obtenir un exemple qui montre comment utiliser le `event` de classe, consultez [comparaison des Structures de données de synchronisation à l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Haut](#top)]

## <a name="related-sections"></a>Rubriques connexes

[Comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Compare le comportement des structures de données de synchronisation à celles fournies par l’API Windows.

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.
