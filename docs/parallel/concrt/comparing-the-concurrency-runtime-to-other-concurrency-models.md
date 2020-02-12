---
title: Comparaison du runtime d'accès concurrentiel aux autres modèles d'accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 5bc6691f6d0b166bb3084091ee6af70474937568
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141329"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Comparaison du runtime d'accès concurrentiel aux autres modèles d'accès concurrentiel

Ce document décrit les différences entre les fonctionnalités et les modèles de programmation du runtime d’accès concurrentiel et d’autres technologies. Il est important de connaître les avantages du runtime d’accès concurrentiel par rapport à ceux des autres modèles de programmation pour choisir la technologie la mieux adaptée aux exigences de vos applications.

Si vous utilisez un autre modèle de programmation, tel que le pool de threads Windows ou OpenMP, vous avez peut-être intérêt à migrer vers le runtime d’accès concurrentiel dans certains cas. La rubrique [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) décrit des exemples de cas où la migration d’OpenMP vers le runtime d’accès concurrentiel peut être bénéfique. Toutefois, si vous êtes satisfait des performances de votre application et de la prise en charge actuelle du débogage, la migration n’est pas obligatoire.

Vous pouvez tirer avantage des fonctionnalités et de la productivité du runtime d’accès concurrentiel pour améliorer votre application existante basée sur un autre modèle d’accès concurrentiel. Le runtime d’accès concurrentiel ne peut pas garantir l’équilibrage du traitement quand plusieurs planificateurs de tâches sont en concurrence pour les mêmes ressources de calcul. Quand il n’y a pas de chevauchement de traitement, l’impact reste toutefois minime.

## <a name="top"></a> Sections

- [Comparaison de la planification préemptive avec la planification coopérative](#models)

- [Comparaison du runtime d’accès concurrentiel avec l’API Windows](#winapi)

- [Comparaison du runtime d’accès concurrentiel avec OpenMP](#openmp)

## <a name="models"></a> Comparaison de la planification préemptive avec la planification coopérative

Le modèle préemptif et les modèles de planification coopérative sont deux méthodes courantes pour permettre à plusieurs tâches de partager des ressources de calcul, par exemple, des processeurs ou des threads matériels.

### <a name="preemptive-and-cooperative-scheduling"></a>Planifications préemptive et coopérative

La*planification préemptive* est un mécanisme de tourniquet (round robin) basé sur des priorités, qui donne à chaque tâche un accès exclusif à une ressource de calcul pour une période donnée, puis bascule vers une autre tâche. La planification préemptive est le modèle généralement utilisé dans les systèmes d’exploitation multitâches tels que Windows. La *planification coopérative* est un mécanisme qui donne à chaque tâche un accès exclusif à une ressource de calcul jusqu’à ce que la tâche se termine ou jusqu’à ce que la tâche donne son accès à la ressource. Le runtime d’accès concurrentiel utilise la planification coopérative en combinaison avec le planificateur préemptif du système d’exploitation pour optimiser l’utilisation des ressources de traitement.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Différences entre les planificateurs préemptifs et coopératifs

Les planificateurs préemptifs cherchent à accorder aux différents threads le même niveau d’accès aux ressources de calcul pour permettre à chaque thread de s’exécuter progressivement. Sur les ordinateurs qui disposent de nombreuses ressources de calcul, l’enjeu n’est pas la distribution équitable des accès, mais l’utilisation efficace des ressources.

Un planificateur préemptif en mode noyau nécessite que le code d’application s’appuie sur le système d’exploitation pour prendre les décisions de planification. Au contraire, un planificateur coopératif en mode utilisateur laisse le code d’application prendre lui-même ses décisions de planification. En permettant à l’application de prendre une grande partie des décisions de planification, la planification coopérative réduit considérablement le traitement lié à la synchronisation en mode noyau. Un planificateur coopératif reporte généralement les décisions de planification sur le noyau du système d’exploitation quand il n’a plus de tâches à planifier. Il reporte également les décisions sur le planificateur du système d’exploitation quand une opération de blocage est communiquée au noyau sans être communiquée au planificateur en mode utilisateur.

### <a name="cooperative-scheduling-and-efficiency"></a>Planification coopérative et efficacité

Pour un planificateur préemptif, tout travail avec le même niveau de priorité est traité de manière égale. Un planificateur préemptif planifie en général les threads dans l’ordre dans lequel ils sont créés. En outre, il accorde à chaque thread une tranche horaire selon le mécanisme du tourniquet (round robin) basé sur la priorité du thread. Ce mécanisme garantit l’équité du traitement des threads (chaque thread progresse), mais cela est au détriment de l’efficacité. Par exemple, de nombreux algorithmes qui utilisent d’importantes ressources de calcul n’ont pas cette exigence d’équité. Ils nécessitent plutôt que les tâches associées se terminent dans le délai le plus court possible. Avec la planification coopérative, une application peut planifier le travail plus efficacement. Prenons l’exemple d’une application qui a de nombreux threads. En planifiant des threads qui ne partagent pas de ressources pour s’exécuter simultanément, vous réduisez le temps de synchronisation et gagnez ainsi en efficacité. Une autre méthode performante pour planifier des tâches consiste à exécuter des pipelines de tâches (où chaque tâche agit sur la sortie de la précédente) sur le même processeur. De cette façon, l’entrée de chaque étape de pipeline est déjà chargée dans le cache mémoire.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Utilisation combinée des planifications préemptive et coopérative

La planification coopérative ne résout pas tous les problèmes de planification. Par exemple, les tâches qui ne basculent pas vers d’autres tâches de manière équitable peuvent consommer toutes les ressources de calcul disponibles et empêcher la progression d’autres tâches. Le runtime d’accès concurrentiel tire parti de l’efficacité de la planification coopérative, en complément des garanties d’équité offertes par la planification préemptive. Par défaut, le runtime d’accès concurrentiel fournit un planificateur coopératif qui utilise un algorithme de vol de travail pour distribuer efficacement le travail entre les ressources de calcul. Toutefois, le planificateur du runtime d’accès concurrentiel s’appuie également sur le planificateur préemptif du système d’exploitation pour distribuer équitablement les ressources entre les applications. Vous pouvez également créer des planificateurs et stratégies de planification personnalisés dans vos applications pour contrôler de manière précise l’exécution des threads.

[[Haut](#top)]

## <a name="winapi"></a> Comparaison du runtime d’accès concurrentiel avec l’API Windows

L’interface de programmation d’application Microsoft Windows, le plus souvent appelée API Windows (et auparavant appelée Win32), fournit un modèle de programmation qui permet l’accès concurrentiel dans vos applications. Le runtime d’accès concurrentiel s’appuie sur l’API Windows pour fournir des modèles de programmation supplémentaires qui ne sont pas disponibles dans le système d’exploitation sous-jacent.

Le runtime d’accès concurrentiel utilise le modèle de thread de l’API Windows pour effectuer le travail parallèle. Il utilise également la gestion de la mémoire Windows API et les mécanismes de stockage local des threads. Sur Windows 7 et Windows Server 2008 R2, il utilise la prise en charge de l’API Windows pour les threads planifiables par l’utilisateur et les ordinateurs avec plus de 64 threads matériels. Le runtime d’accès concurrentiel étend le modèle de l’API Windows en fournissant un planificateur de tâches coopératif et un algorithme de vol de travail pour optimiser l’utilisation des ressources de calcul, et en autorisant l’exécution de plusieurs instances simultanées du planificateur.

### <a name="programming-languages"></a>Langages de programmation

L’API Windows utilise le langage de programmation C pour exposer le modèle de programmation. Le runtime d’accès concurrentiel fournit une interface de programmation C++ qui tire parti des nouvelles fonctionnalités du langage C++. Par exemple, les fonctions lambda fournissent un mécanisme succinct de type sécurisé pour la définition des fonctions de travail parallèles. Pour plus d’informations sur les nouvelles fonctionnalités C++ utilisées par le runtime d’accès concurrentiel, consultez [Vue d’ensemble](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Threads et pools de threads

Le thread est au cœur du mécanisme d’accès concurrentiel dans l’API Windows. Les threads sont généralement créés à l’aide de la fonction [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) . Les threads sont relativement faciles à créer et à utiliser, mais pour leur gestion, le système d’exploitation alloue une quantité importante de temps et d’autres ressources. Même si chaque thread est assuré d’obtenir le même temps d’exécution que les autres threads au même niveau de priorité, vous devez aussi créer des tâches suffisamment grandes pour prendre en charge le traitement induit. Pour des tâches plus petites ou plus précises, le traitement lié à l’accès concurrentiel peut annuler les avantages de l’exécution des tâches en parallèle.

Les pools de threads sont un moyen de réduire le coût de gestion des threads. Les pools de threads personnalisés et l’implémentation du pool de threads fournie par l’API Windows permettent à de petits éléments de travail de s’exécuter efficacement en parallèle. Le pool de threads Windows met les éléments de travail en attente selon le principe du premier entré, premier sorti (FIFO). Chaque élément de travail est démarré dans l’ordre dans lequel il a été ajouté au pool.

Le runtime d’accès concurrentiel implémente un algorithme de vol de travail pour étendre le mécanisme de planification FIFO. L’algorithme déplace les tâches qui n’ont pas encore commencé vers des threads qui n’ont plus d’éléments de travail à exécuter. L’algorithme de vol de travail permet d’équilibrer le traitement du travail, mais il peut aussi provoquer un reclassement des éléments de travail. À cause de ce processus de reclassement, un élément de travail peut ne pas démarrer dans l’ordre dans lequel il a été envoyé. Cela est utile avec les algorithmes récursifs, où les données ont plus de chance d’être partagées entre des tâches récentes que parmi les tâches plus anciennes. L’exécution des nouveaux éléments en premier diminue le nombre de défauts de cache et, éventuellement, le nombre de défauts de page.

Du point de vue du système d’exploitation, le vol de travail n’est pas équitable. Toutefois, quand une application implémente un algorithme ou une tâche à exécuter en parallèle, l’équité parmi les sous-tâches n’a parfois pas d’importance. C’est la rapidité avec laquelle la tâche globale se termine qui est importante. Pour d’autres algorithmes, le principe du premier entré, premier sorti (FIFO) est la stratégie de planification appropriée.

### <a name="behavior-on-various-operating-systems"></a>Comportement sur différents systèmes d’exploitation

Sur Windows XP et Windows Vista, les applications qui utilisent le runtime d’accès concurrentiel se comportent de façon similaire, mais les performances des tas sont meilleures sur Windows Vista.

Sur Windows 7 et Windows Server 2008 R2, le système d’exploitation prend mieux en charge l’accès concurrentiel et la scalabilité. Par exemple, ces systèmes d’exploitation prennent en charge les ordinateurs qui ont plus de 64 threads matériels. Une application existante qui utilise l’API Windows doit être modifiée pour tirer parti de ces nouvelles fonctionnalités. En revanche, une application qui utilise le runtime d’accès concurrentiel utilise automatiquement ces fonctionnalités, sans nécessiter de modifications.

[base.user-mode_scheduling](/windows/win32/procthread/user-mode-scheduling)

[[Haut](#top)]

## <a name="openmp"></a> Comparaison du runtime d’accès concurrentiel avec OpenMP

Le runtime d’accès concurrentiel accepte divers modèles de programmation. Ces modèles peuvent chevaucher ou compléter les modèles d’autres bibliothèques. Cette section compare le runtime d’accès concurrentiel avec [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

Le modèle de programmation OpenMP est défini par une norme ouverte et a des liaisons bien définies aux langages de programmation C/C++ et Fortran. Les versions 2.0 et 2.5 d’OpenMP sont adaptées pour les algorithmes parallèles itératifs (autrement dit, ceux qui effectuent une itération parallèle sur un tableau de données). OpenMP montre une efficacité optimale quand le degré de parallélisme est prédéterminé et correspond aux ressources disponibles sur le système. Le modèle OpenMP est particulièrement approprié pour les calculs haute performance, où de très grandes tâches de calcul sont distribuées entre les ressources de traitement d’un seul ordinateur. Dans ce scénario, l’environnement matériel est connu et le développeur peut raisonnablement s’attendre à avoir un accès exclusif aux ressources de calcul lors de l’exécution de l’algorithme.

Le modèle OpenMP n’est pas forcément optimal pour les environnements informatiques avec moins de contraintes. Par exemple, les tâches récursives (comme l’algorithme de tri rapide ou la recherche dans une arborescence de données) sont plus difficiles à implémenter avec OpenMP. Le runtime d’accès concurrentiel étend les fonctionnalités d’OpenMP en fournissant la [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) et la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md). Contrairement à OpenMP, le runtime d’accès concurrentiel fournit un planificateur dynamique qui s’adapte aux ressources disponibles et ajuste le degré de parallélisme en fonction du traitement nécessaire.

La plupart des fonctionnalités du runtime d’accès concurrentiel peuvent être étendues. Vous pouvez également combiner des fonctionnalités existantes pour en composer de nouvelles. OpenMP repose sur des directives de compilateur et ne peut donc pas être étendu facilement.

Pour plus d’informations sur les différences entre le runtime d’accès concurrentiel et OpenMP, et sur la migration du code OpenMP existant pour utiliser le runtime d’accès concurrentiel, consultez [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
[Vue d'ensemble](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
