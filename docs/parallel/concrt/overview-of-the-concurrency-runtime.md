---
description: 'En savoir plus sur : vue d’ensemble des runtime d’accès concurrentiel'
title: Vue d'ensemble du runtime d'accès concurrentiel
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: b6ff531b1961b32056a7232b62eca05d7a8793b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189156"
---
# <a name="overview-of-the-concurrency-runtime"></a>Vue d'ensemble du runtime d'accès concurrentiel

Ce document fournit une vue d'ensemble du runtime d'accès concurrentiel. Il décrit les avantages du runtime d'accès concurrentiel, quand l'utiliser et la façon dont ses composants interagissent entre eux et avec le système d'exploitation et les applications.

## <a name="sections"></a><a name="top"></a> Sections

Ce document contient les sections suivantes :

- [Historique d’implémentation runtime d’accès concurrentiel](#dlls)

- [Pourquoi un runtime d'accès concurrentiel est-il important ?](#runtime)

- [Architecture](#architecture)

- [Expressions lambda C++](#lambda)

- [Configuration requise](#requirements)

## <a name="concurrency-runtime-implementation-history"></a><a name="dlls"></a> Historique d’implémentation runtime d’accès concurrentiel

Dans Visual Studio 2010 à 2013, le runtime d’accès concurrentiel a été incorporé dans msvcr100.dll par le biais de msvcr120.dll.  Quand la refactorisation UCRT s’est produite dans Visual Studio 2015, cette DLL a été refactorie en trois parties :

- API ucrtbase.dll – C, fournie dans Windows 10 et de niveau inférieur par le biais de Windows Update-

- vcruntime140.dll – fonctions de prise en charge du compilateur et du runtime EH, fournies par le biais de Visual Studio

- concrt140.dll – runtime d’accès concurrentiel, fourni via Visual Studio. Requis pour les conteneurs et les algorithmes parallèles tels que `concurrency::parallel_for` . En outre, la bibliothèque STL requiert que cette DLL sur Windows XP utilise des primitives de synchronisation de l’alimentation, car Windows XP n’a pas de variables de condition.

Dans Visual Studio 2015 et versions ultérieures, le planificateur de tâches du runtime d'accès concurrentiel n'est plus le planificateur de la classe de tâche et des types associés dans ppltasks.h. Ces types utilisent désormais le pool de threads Windows pour de meilleures performances et une meilleure interopérabilité avec les primitives de synchronisation Windows.

## <a name="why-a-runtime-for-concurrency-is-important"></a><a name="runtime"></a> Pourquoi un Runtime pour l’accès concurrentiel est-il important ?

Un runtime d'accès concurrentiel fournit l'uniformité et la prévisibilité aux applications et à leurs composants qui s'exécutent simultanément. Deux exemples des avantages du runtime d’accès concurrentiel sont la *planification des tâches coopératives* et le *blocage coopératif*.

Le runtime d'accès concurrentiel utilise un planificateur de tâches coopératif qui implémente un algorithme de vol de travail pour distribuer efficacement le travail entre les ressources informatiques. Par exemple, considérez une application qui a deux threads gérés par le même runtime. Si un thread termine sa tâche planifiée, il peut décharger du travail de l’autre thread. Ce mécanisme équilibre la charge de travail globale de l'application.

Le runtime d’accès concurrentiel fournit également des primitives de synchronisation qui utilisent le blocage coopératif pour synchroniser l’accès aux ressources. Par exemple, considérez une tâche qui doit avoir un accès exclusif à une ressource partagée. Par un blocage coopératif, le runtime peut utiliser le quantum restant pour effectuer une autre tâche, pendant que la première tâche attend la ressource. Ce mécanisme favorise l'utilisation maximale des ressources informatiques.

[[Haut](#top)]

## <a name="architecture"></a><a name="architecture"></a> Architecture

Le runtime d'accès concurrentiel se divise en quatre composants : la bibliothèque de modèles parallèles (PPL), la bibliothèque d'agents asynchrones, le planificateur de tâches et le gestionnaire des ressources. Ces composants résident entre le système d'exploitation et les applications. L'illustration suivante montre comment les composants du runtime d'accès concurrentiel interagit entre le système d'exploitation et les applications :

**Architecture du runtime d'accès concurrentiel**

![Architecture de runtime d'accès concurrentiel](../../parallel/concrt/media/concurrencyrun.png "Architecture de runtime d'accès concurrentiel")

> [!IMPORTANT]
> Les composants Planificateur de tâches et Gestionnaire des ressources ne sont pas disponibles à partir d’une application plateforme Windows universelle (UWP) ou lorsque vous utilisez la classe de tâche ou d’autres types dans ppltasks. h.

La runtime d’accès concurrentiel est très *composable*, autrement dit, vous pouvez combiner les fonctionnalités existantes pour en faire plus. Le runtime d’accès concurrentiel compose de nombreuses fonctionnalités, telles que des algorithmes parallèles, à partir de composants de niveau inférieur.

Le runtime d’accès concurrentiel fournit également des primitives de synchronisation qui utilisent le blocage coopératif pour synchroniser l’accès aux ressources. Pour plus d’informations sur ces primitives de synchronisation, consultez [structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md).

Les sections suivantes fournissent un bref aperçu de ce que fournit chaque composant et quand les utiliser.

### <a name="parallel-patterns-library"></a>bibliothèque de modèles parallèles

La bibliothèque de modèles parallèles (PPL) fournit des algorithmes et des conteneurs à usage général pour effectuer un parallélisme affiné. La bibliothèque de modèles parallèles active le *parallélisme de données impératif* en fournissant des algorithmes parallèles qui distribuent des calculs sur des collections ou sur des jeux de données à travers des ressources informatiques. Il active également le *parallélisme des tâches* en fournissant des objets de tâche qui répartissent plusieurs opérations indépendantes sur les ressources de calcul.

Utilisez la bibliothèque de modèles parallèles quand vous avez un calcul local qui peut tirer parti d’une exécution en parallèle. Par exemple, vous pouvez utiliser l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour transformer une **`for`** boucle existante afin qu’elle agisse en parallèle.

Pour plus d’informations sur la bibliothèque de modèles parallèles, consultez [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>bibliothèque d’agents asynchrones

La bibliothèque d’agents asynchrones (ou simplement la *bibliothèque d’agents*) fournit à la fois un modèle de programmation basé sur acteur et des interfaces de passage de messages pour les tâches de flux de données de granularité grossière et de traitement pipeline. Les agents asynchrones vous permettent d'utiliser de façon productive la latence, en effectuant le travail pendant que d'autres composants attendent des données.

Utilisez la bibliothèque d'agents quand vous avez plusieurs entités qui communiquent entre elles de façon asynchrone. Par exemple, vous pouvez créer un agent qui lit des données à partir d'un fichier ou d'une connexion réseau, puis utilise les interfaces de passage de messages pour envoyer ces données à un autre agent.

Pour plus d’informations sur la bibliothèque d’agents, consultez [Asynchronous agents Library](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Planificateur de tâches

Le planificateur de tâches planifie et coordonne les tâches au moment de l'exécution. Il est coopératif et utilise un algorithme de vol de travail pour optimiser l'utilisation des ressources de traitement.

Le runtime d'accès concurrentiel fournit un planificateur par défaut pour que vous n'ayez pas à gérer les détails de l'infrastructure. Toutefois, pour répondre aux besoins de qualité de votre application, vous pouvez également fournir votre propre stratégie de planification ou associer des planificateurs spécifiques à des tâches spécifiques.

Pour plus d’informations sur la Planificateur de tâches, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Gestionnaire de ressources

Le rôle du gestionnaire des ressources est de gérer les ressources informatiques, comme les processeurs et la mémoire. Le gestionnaire des ressources répond aux charges de travail à mesure qu'elles changent au moment de l'exécution en affectant des ressources là où elles peuvent être les plus efficaces.

Le gestionnaire des ressources sert d’abstraction sur les ressources informatiques et interagit principalement avec le planificateur de tâches. Bien que vous puissiez utiliser le gestionnaire des ressources pour ajuster les performances de vos bibliothèques et applications, vous utilisez généralement la fonctionnalité fournie par la bibliothèque de modèles parallèles, la bibliothèque d'agents et le planificateur de tâches. Ces bibliothèques utilisent le gestionnaire des ressources pour rééquilibrer de manière dynamique les ressources à mesure que les charges de travail évoluent.

[[Haut](#top)]

## <a name="c-lambda-expressions"></a><a name="lambda"></a> Expressions lambda C++

La plupart des types et algorithmes définis par le runtime d'accès concurrentiel sont implémentés en tant que modèles C++. Certains de ces types et algorithmes prennent comme paramètre une routine qui effectue le travail. Ce paramètre peut être une fonction lambda, un objet de fonction ou un pointeur de fonction. Ces entités sont également appelées *fonctions de travail* ou *routines de travail*.

Les expressions lambda sont une nouvelle fonctionnalité importante du langage Visual C++, car elles offrent un moyen concis de définir des fonctions de travail pour un traitement parallèle. Les objets de fonction et les pointeurs de fonction vous permettent d'utiliser le runtime d'accès concurrentiel avec votre code existant. Toutefois, nous vous recommandons d'utiliser des expressions lambda quand vous écrivez un nouveau code en raison des avantages en matière de sécurité et de productivité qu'elles apportent.

L’exemple suivant compare la syntaxe des fonctions lambda, des objets de fonction et des pointeurs de fonction dans plusieurs appels à l’algorithme d' [accès concurrentiel ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) . Chaque appel à `parallel_for_each` utilise une technique différente pour calculer le carré de chaque élément dans un objet [std :: Array](../../standard-library/array-class-stl.md) .

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Sortie**

```Output
1
256
6561
65536
390625
```

Pour plus d’informations sur les fonctions lambda en C++, consultez [expressions lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Haut](#top)]

## <a name="requirements"></a><a name="requirements"></a> Spécifications

Le tableau suivant présente les fichiers d'en-tête associés à chaque composant du runtime d'accès concurrentiel :

|Composant|Fichiers d’en-tête|
|---------------|------------------|
|Bibliothèque de modèles parallèles|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|bibliothèque d’agents asynchrones|agents.h|
|Planificateur de tâches|concrt.h|
|Gestionnaire de ressources|concrtrm.h|

Le runtime d’accès concurrentiel est déclaré dans l’espace de noms d' [accès concurrentiel](../../parallel/concrt/reference/concurrency-namespace.md) . (Vous pouvez également utiliser la [concurrence](../../parallel/concrt/reference/concurrency-namespace.md), qui est un alias pour cet espace de noms.) L' `concurrency::details` espace de noms prend en charge l’infrastructure runtime d’accès concurrentiel et n’est pas destiné à être utilisé directement à partir de votre code.

Le runtime d'accès concurrentiel est fourni dans le cadre de la bibliothèque Runtime C (CRT). Pour plus d’informations sur la création d’une application qui utilise le CRT, consultez fonctionnalités de la [bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

[[Haut](#top)]
