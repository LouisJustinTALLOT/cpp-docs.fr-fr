---
title: Structures de données de synchronisation
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 85dec6b003330a3560ae1dcc5c41b5e6d49f765e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142803"
---
# <a name="synchronization-data-structures"></a>Structures de données de synchronisation

L’runtime d’accès concurrentiel fournit plusieurs structures de données qui vous permettent de synchroniser l’accès aux données partagées à partir de plusieurs threads. Ces structures de données sont utiles quand vous avez des données partagées que vous modifiez rarement. Un objet de synchronisation, par exemple une section critique, entraîne l’attente d’autres threads jusqu’à ce que la ressource partagée soit disponible. Par conséquent, si vous utilisez un tel objet pour synchroniser l’accès aux données fréquemment utilisées, vous pouvez perdre l’extensibilité dans votre application. La [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) fournit la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) , qui vous permet de partager une ressource entre plusieurs threads ou tâches sans nécessiter de synchronisation. Pour plus d’informations sur la classe `combinable`, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="top"></a> Sections

Cette rubrique décrit en détail les types de blocs de messages asynchrones suivants :

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock et scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a>critical_section

La classe [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md) représente un objet d’exclusion mutuelle coopérative qui donne à d’autres tâches au lieu de les préemption. Les sections critiques sont utiles lorsque plusieurs threads requièrent un accès exclusif en lecture et en écriture aux données partagées.

La classe `critical_section` est non réentrante. La méthode [Concurrency :: critical_section :: Lock](reference/critical-section-class.md#lock) lève une exception de type [Concurrency :: improper_lock](../../parallel/concrt/reference/improper-lock-class.md) si elle est appelée par le thread qui possède déjà le verrou.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente les méthodes importantes définies par la classe `critical_section`.

|Méthode|Description|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Acquiert la section critique. Le contexte d’appel se bloque jusqu’à ce qu’il acquière le verrou.|
|[try_lock](reference/critical-section-class.md#try_lock)|Tente d’acquérir la section critique, mais ne se bloque pas.|
|[unlock](reference/critical-section-class.md#unlock)|Libère la section critique.|

[[Haut](#top)]

## <a name="reader_writer_lock"></a>reader_writer_lock

La classe [Concurrency :: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) fournit des opérations de lecture/écriture thread-safe aux données partagées. Utilisez des verrous en lecture/écriture lorsque plusieurs threads requièrent un accès en lecture simultané à une ressource partagée, mais écrivent rarement dans cette ressource partagée. Cette classe fournit à tout moment un seul thread d’accès en écriture à un objet.

La classe `reader_writer_lock` peut être plus performante que la classe `critical_section`, car un objet `critical_section` acquiert un accès exclusif à une ressource partagée, ce qui empêche l’accès en lecture simultané.

À l’instar de la classe `critical_section`, la classe `reader_writer_lock` représente un objet d’exclusion mutuelle coopérative qui donne à d’autres tâches au lieu de les préemption.

Quand un thread qui doit écrire dans une ressource partagée acquiert un verrou de lecture/écriture, les autres threads qui doivent également accéder à la ressource sont bloqués jusqu’à ce que l’enregistreur libère le verrou. La classe `reader_writer_lock` est un exemple de verrou de *préférence en écriture* , qui est un verrou qui débloque les enregistreurs en attente avant de débloquer les lecteurs en attente.

À l’instar de la classe `critical_section`, la classe `reader_writer_lock` n’est pas réentrante. Les méthodes [Concurrency :: reader_writer_lock :: Lock](reference/reader-writer-lock-class.md#lock) et [Concurrency :: reader_writer_lock :: lock_read](reference/reader-writer-lock-class.md#lock_read) lèvent une exception de type `improper_lock` si elles sont appelées par un thread qui détient déjà le verrou.

> [!NOTE]
> Étant donné que la classe de `reader_writer_lock` n’est pas réentrante, vous ne pouvez pas mettre à niveau un verrou en lecture seule vers un verrou de lecture/écriture, ni rétrograder un verrou de lecture/écriture à un verrou en lecture seule. L’exécution de l’une de ces opérations produit un comportement non spécifié.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente les méthodes importantes définies par la classe `reader_writer_lock`.

|Méthode|Description|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Acquiert un accès en lecture/écriture au verrou.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Tente d’acquérir l’accès en lecture/écriture au verrou, mais ne bloque pas.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Acquiert un accès en lecture seule au verrou.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Tente d’acquérir un accès en lecture seule au verrou, mais ne bloque pas.|
|[unlock](reference/reader-writer-lock-class.md#unlock)|Libère le verrou.|

[[Haut](#top)]

## <a name="scoped_lock"></a>scoped_lock et scoped_lock_read

Les classes `critical_section` et `reader_writer_lock` fournissent des classes d’assistance imbriquées qui simplifient la façon dont vous travaillez avec les objets d’exclusion mutuelle. Ces classes d’assistance sont appelées *verrous étendus*.

La classe `critical_section` contient la classe [Concurrency :: critical_section :: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) . Le constructeur acquiert l’accès à l’objet `critical_section` fourni ; le destructeur libère l’accès à cet objet. La classe `reader_writer_lock` contient la classe [Concurrency :: reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) , qui ressemble à `critical_section::scoped_lock`, sauf qu’elle gère l’accès en écriture à l’objet `reader_writer_lock` fourni. La classe `reader_writer_lock` contient également la classe [Concurrency :: reader_writer_lock :: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) . Cette classe gère l’accès en lecture à l’objet `reader_writer_lock` fourni.

Les verrous délimités présentent plusieurs avantages lorsque vous utilisez `critical_section` et `reader_writer_lock` des objets manuellement. En général, vous allouez un verrou étendu sur la pile. Un verrou étendu libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit ; par conséquent, vous ne Déverrouillez pas manuellement l’objet sous-jacent. Cela est utile lorsqu’une fonction contient plusieurs instructions `return`. Les verrous délimités peuvent également vous aider à écrire du code sécurisé. Quand une instruction `throw` provoque le déroulement de la pile, le destructeur pour tout verrou d’étendue active est appelé, et par conséquent l’objet exclusion mutuelle est toujours correctement libéré.

> [!NOTE]
> Lorsque vous utilisez les classes `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`et `reader_writer_lock::scoped_lock_read`, ne libérez pas manuellement l’accès à l’objet exclusion mutuelle sous-jacent. Cela peut mettre le runtime dans un État non valide.

## <a name="event"></a>événement

La classe [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) représente un objet de synchronisation dont l’État peut être signalé ou non signalé. Contrairement aux objets de synchronisation, tels que les sections critiques, dont l’objectif est de protéger l’accès aux données partagées, les événements synchronisent le déroulement de l’exécution.

La classe `event` est utile lorsqu’une tâche a terminé le travail pour une autre tâche. Par exemple, une tâche peut signaler une autre tâche qu’elle a lu des données à partir d’une connexion réseau ou d’un fichier.

### <a name="methods-and-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente plusieurs des méthodes importantes définies par la classe `event`.

|Méthode|Description|
|------------|-----------------|
|[qu'](reference/event-class.md#wait)|Attend que l’événement soit signalé.|
|[set](reference/event-class.md#set)|Définit l’événement à l’état signalé.|
|[reset](reference/event-class.md#reset)|Définit l’événement à l’état non signalé.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Attend que plusieurs événements soient signalés.|

### <a name="example"></a>Exemple

Pour obtenir un exemple qui montre comment utiliser la classe `event`, consultez [comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Haut](#top)]

## <a name="related-sections"></a>Sections connexes

[Comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Compare le comportement des structures de données de synchronisation à ceux fournis par l’API Windows.

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.
