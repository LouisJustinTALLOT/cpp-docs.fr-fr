---
title: Meilleures pratiques de la Bibliothèque de modèles parallèles
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 641d85b03fca13a6592610d87563e3e701ad3e3e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419167"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Meilleures pratiques de la Bibliothèque de modèles parallèles

Ce document décrit la meilleure façon d’utiliser efficacement la bibliothèque de modèles parallèles (PPL). La bibliothèque de modèles parallèles (PPL) fournit des conteneurs, des objets et des algorithmes à usage général pour effectuer un parallélisme affiné.

Pour plus d’informations sur la bibliothèque PPL, consultez [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="top"></a> Sections

Ce document contient les sections suivantes :

- [Ne pas paralléliser les petits corps de boucle](#small-loops)

- [Parallélisme Express au niveau le plus élevé possible](#highest)

- [Utilisez parallel_invoke pour résoudre les problèmes de division et de conquête](#divide-and-conquer)

- [Utiliser l’annulation ou la gestion des exceptions pour rompre une boucle parallèle](#breaking-loops)

- [Comprendre comment l’annulation et la gestion des exceptions affectent la destruction d’objets](#object-destruction)

- [Ne pas bloquer de façon répétée dans une boucle parallèle](#repeated-blocking)

- [Ne pas effectuer d’opérations de blocage lorsque vous annulez un travail parallèle](#blocking)

- [Ne pas écrire dans les données partagées dans une boucle parallèle](#shared-writes)

- [Dans la mesure du possible, évitez le faux partage](#false-sharing)

- [S’assurer que les variables sont valides pendant toute la durée de vie d’une tâche](#lifetime)

## <a name="small-loops"></a>Ne pas paralléliser les petits corps de boucle

La parallélisation des corps de boucles relativement petites peut entraîner une surcharge de la planification associée pour compenser les avantages du traitement parallèle. Prenons l'exemple suivant, qui ajoute chaque paire d'éléments dans deux tableaux.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

La charge de travail de chaque itération de boucle parallèle est trop petite pour bénéficier de la surcharge de traitement parallèle. Vous pouvez améliorer les performances de cette boucle en effectuant plus de travail dans le corps de la boucle ou en exécutant la boucle en série.

[[Haut](#top)]

## <a name="highest"></a>Parallélisme Express au niveau le plus élevé possible

Quand vous parallélisez du code uniquement au niveau inférieur, vous pouvez introduire une construction de bifurcation-jointure qui n'évolue pas au fur et à mesure que le nombre de processeurs augmente. Une construction de *bifurcation-jointure* est une construction dans laquelle une tâche divise son travail en sous-tâches parallèles plus petites et attend que ces sous-tâches se terminent. Chaque sous-tâche peut elle-même se diviser de manière récursive en sous-tâches supplémentaires.

Bien que le modèle de bifurcation-jointure puisse s’avérer utile pour résoudre de nombreux problèmes, dans certaines situations, la surcharge de synchronisation peut réduire l’évolutivité. Par exemple, considérez le code en série suivant qui traite des données d'image.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Étant donné que chaque itération de boucle est indépendante, vous pouvez paralléliser une grande partie du travail, comme indiqué dans l'exemple suivant. Cet exemple utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour paralléliser la boucle externe.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

L'exemple suivant illustre une construction de bifurcation-jointure en appelant la fonction `ProcessImage` dans une boucle. Chaque appel à `ProcessImage` ne retourne rien tant que chaque sous-tâche n'est pas terminée.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

Si chaque itération de la boucle parallèle n'exécute quasiment aucun travail ou si le travail effectué par la boucle parallèle est déséquilibré, c'est-à-dire que certaines itérations de boucle prennent plus de temps que d'autres, la surcharge de planification requise pour la bifurcation et la jointure fréquentes du travail peut l'emporter sur l'avantage d'une exécution parallèle. Cette surcharge augmente à mesure que le nombre de processeurs augmente.

Pour réduire la quantité de surcharge de planification dans cet exemple, vous pouvez paralléliser les boucles externes avant de paralléliser les boucles internes ou utiliser une autre construction parallèle comme le traitement « pipeline ». L’exemple suivant modifie la fonction `ProcessImages` pour utiliser l’algorithme d' [arallel_for_each d’accès concurrentiel ::p](reference/concurrency-namespace-functions.md#parallel_for_each) pour paralléliser la boucle externe.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

Pour obtenir un exemple similaire qui utilise un pipeline pour effectuer le traitement d’image en parallèle, consultez [procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Haut](#top)]

## <a name="divide-and-conquer"></a>Utilisez parallel_invoke pour résoudre les problèmes de division et de conquête

Un problème de *Division et de conquête* est une forme de la construction de bifurcation-jointure qui utilise la récursivité pour diviser une tâche en sous-tâches. Outre les classes [Concurrency :: task_group](reference/task-group-class.md) et [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , vous pouvez également utiliser l’algorithme de [arallel_invoke d’accès concurrentiel ::p](reference/concurrency-namespace-functions.md#parallel_invoke) pour résoudre les problèmes de division et de conquête. L’algorithme `parallel_invoke` a une syntaxe plus succincte que les objets de groupes de tâches. Il s’avère utile quand vous avez un nombre fixe de tâches parallèles.

L'exemple suivant illustre l'utilisation de l'algorithme `parallel_invoke` pour implémenter l'algorithme de tri bitonique.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Pour réduire la surcharge, l’algorithme `parallel_invoke` effectue la dernière série de tâches sur le contexte d’appel.

Pour obtenir la version complète de cet exemple, consultez [Comment : utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Pour plus d’informations sur l’algorithme `parallel_invoke`, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

[[Haut](#top)]

## <a name="breaking-loops"></a>Utiliser l’annulation ou la gestion des exceptions pour rompre une boucle parallèle

La bibliothèque de modèles parallèles fournit deux méthodes pour annuler un travail parallèle exécuté par un groupe de tâches ou un algorithme parallèle. L’une des méthodes consiste à utiliser le mécanisme d’annulation fourni par les classes [Concurrency :: task_group](reference/task-group-class.md) et [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) . La seconde consiste à lever une exception dans le corps d'une fonction de travail de tâche. Le mécanisme d’annulation est plus efficace que la gestion des exceptions pour annuler une arborescence de travail parallèle. Une *arborescence de travail parallèle* est un groupe de groupes de tâches connexes dans lequel certains groupes de tâches contiennent d’autres groupes de tâches. Le mécanisme d'annulation annule un groupe de tâches et ses groupes de tâches enfants de haut en bas. À l’inverse, la gestion des exceptions fonctionne de bas en haut et doit annuler chaque groupe de tâches enfant indépendamment puisque l’exception se propage vers le haut.

Quand vous travaillez directement avec un objet de groupe de tâches, utilisez les méthodes [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) ou [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) pour annuler le travail qui appartient à ce groupe de tâches. Pour annuler un algorithme parallèle, par exemple, `parallel_for`, créez un groupe de tâches parent et annulez ce groupe de tâches. Par exemple, considérez la fonction suivante, `parallel_find_any`, qui recherche une valeur dans un tableau en parallèle.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Étant donné que les algorithmes parallèles utilisent des groupes de tâches, quand l'une des itérations parallèles annule le groupe de tâches parent, la tâche globale est annulée. Pour obtenir la version complète de cet exemple, consultez [Comment : utiliser l’annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

Bien que la gestion des exceptions soit moins efficace pour annuler un travail parallèle que le mécanisme d'annulation, dans certains cas, elle est appropriée. Par exemple, la méthode suivante, `for_all`, exécute une fonction de travail de manière récursive sur chaque nœud d'une structure `tree`. Dans cet exemple, le membre de données `_children` est un [std :: List](../../standard-library/list-class.md) qui contient des objets `tree`.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

L’appelant de la méthode `tree::for_all` peut lever une exception s’il n’a pas besoin que la fonction de travail soit appelée sur chaque élément de l’arborescence. L'exemple suivant illustre la fonction `search_for_value`, qui recherche une valeur dans l'objet `tree` fourni. La fonction `search_for_value` utilise une fonction de travail qui lève une exception quand l’élément actuel de l’arborescence correspond à la valeur fournie. La fonction `search_for_value` utilise un bloc `try-catch` pour capturer l'exception et imprimer le résultat dans la console.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Pour obtenir la version complète de cet exemple, consultez [Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Pour plus d’informations générales sur les mécanismes d’annulation et de gestion des exceptions fournis par la bibliothèque de modèles parallèles, consultez [annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md) et [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[[Haut](#top)]

## <a name="object-destruction"></a>Comprendre comment l’annulation et la gestion des exceptions affectent la destruction d’objets

Dans une arborescence de travail parallèle, une tâche qui est annulée empêche les tâches enfants de s'exécuter. Des problèmes peuvent alors survenir si l'une des tâches enfants effectue une opération importante pour votre application, comme la libération d'une ressource. De plus, l’annulation d’une tâche peut déclencher la propagation d’une exception via un destructeur d’objet et entraîner un comportement non défini dans votre application.

Dans l'exemple suivant, la classe `Resource` décrit une ressource et la classe `Container` décrit un conteneur qui contient des ressources. Dans son destructeur, la classe `Container` appelle la méthode `cleanup` sur deux de ses membres `Resource` en parallèle, puis appelle la méthode `cleanup` sur son troisième membre `Resource`.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

Bien que ce modèle ne présente aucun problème particulier, considérez le code suivant qui exécute deux tâches en parallèle. La première tâche crée un objet `Container` et la seconde annule la tâche globale. À titre d’illustration, l’exemple utilise deux objets [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) pour s’assurer que l’annulation se produit après la création de l’objet `Container` et que l’objet `Container` est détruit une fois l’opération d’annulation effectuée.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Cet exemple produit la sortie suivante :

```Output
Container 1: Freeing resources...Exiting program...
```

Cet exemple de code contient les problèmes suivants susceptibles d'entraîner un comportement différent de celui que vous attendez :

- L’annulation de la tâche parente entraîne également l’annulation de la tâche enfant, à laquelle l’appel d' [accès concurrentiel ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke). Ainsi, ces deux ressources ne sont pas libérées.

- L’annulation de la tâche parente amène la tâche enfant à lever une exception interne. Étant donné que le destructeur `Container` ne gère pas cette exception, l'exception est propagée vers le haut et la troisième ressource n'est pas libérée.

- L’exception qui est levée par la tâche enfant se propage via le destructeur `Container`. La levée à partir d'un destructeur met l'application dans un état non défini.

Nous vous recommandons de ne pas effectuer d'opérations critiques, comme la libération de ressources, dans des tâches, sauf si vous pouvez garantir que ces tâches ne seront pas annulées. Nous vous recommandons également de ne pas utiliser de fonctionnalités runtime pouvant se déclencher dans le destructeur de vos types.

[[Haut](#top)]

## <a name="repeated-blocking"></a>Ne pas bloquer de façon répétée dans une boucle parallèle

Une boucle parallèle telle que la [concurrence ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) ou la [concurrence ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) qui est dominée par les opérations bloquantes peut entraîner la création de nombreux threads sur une brève période.

Le runtime d'accès concurrentiel effectue un travail supplémentaire quand une tâche se termine, se bloque ou génère un résultat de manière coopérative. Quand une itération de boucle parallèle se bloque, le runtime peut démarrer une autre itération. Quand il n'existe aucun thread inactif disponible, le runtime crée un thread.

Quand le corps d'une boucle parallèle se bloque de temps en temps, ce mécanisme permet d'optimiser le débit global de la tâche. Toutefois, quand de nombreuses itérations se bloquent, le runtime peut créer de nombreux threads pour exécuter le travail supplémentaire. Cela peut entraîner des conditions de mémoire insuffisante ou une mauvaise utilisation des ressources matérielles.

Prenons l’exemple suivant qui appelle la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) dans chaque itération d’une boucle `parallel_for`. Étant donné que `send` se bloque de manière coopérative, le runtime crée un thread pour exécuter le travail supplémentaire chaque fois que `send` est appelé.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Nous vous recommandons de refactoriser votre code pour éviter ce modèle. Dans cet exemple, vous pouvez éviter la création de threads supplémentaires en appelant `send` dans une boucle `for` en série.

[[Haut](#top)]

## <a name="blocking"></a>Ne pas effectuer d’opérations de blocage lorsque vous annulez un travail parallèle

Dans la mesure du possible, n’effectuez pas d’opérations de blocage avant d’appeler la méthode [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) ou [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) pour annuler un travail parallèle.

Quand une tâche effectue une opération de blocage coopérative, le runtime peut effectuer un autre travail pendant que la première tâche attend des données. Le runtime replanifie la tâche qui attend quand elle se débloque. En général, le runtime replanifie les dernières tâches qui ont été débloquées avant de replanifier celles qui l’ont été auparavant. Ainsi, le runtime peut planifier du travail inutile lors de l'opération de blocage, ce qui entraîne une diminution des performances. En conséquence, quand vous effectuez une opération de blocage avant d'annuler un travail parallèle, celle-ci peut retarder l'appel à `cancel`. Cette opération amène d'autres tâches à effectuer du travail inutile.

Prenons l'exemple suivant qui définit la fonction `parallel_find_answer`, qui recherche un élément du tableau fourni qui satisfait à la fonction de prédicat fournie. Lorsque la fonction de prédicat retourne la **valeur true**, la fonction de travail parallèle crée un objet `Answer` et annule la tâche globale.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

L'opérateur `new` effectue une allocation de tas, qui peut se bloquer. Le Runtime effectue un autre travail uniquement lorsque la tâche effectue un appel de blocage coopératif, tel qu’un appel à [Concurrency :: critical_section :: Lock](reference/critical-section-class.md#lock).

L'exemple suivant montre comment empêcher le travail inutile et ainsi améliorer les performances. Cet exemple annule le groupe de tâches avant qu’il alloue le stockage pour l’objet `Answer`.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[Haut](#top)]

## <a name="shared-writes"></a>Ne pas écrire dans les données partagées dans une boucle parallèle

L’runtime d’accès concurrentiel fournit plusieurs structures de données, par exemple [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md), qui synchronisent l’accès simultané aux données partagées. Ces structures de données s'avèrent utiles dans de nombreux cas, par exemple, quand plusieurs tâches requièrent peu souvent un accès partagé à une ressource.

Prenons l’exemple suivant, qui utilise l’algorithme d' [accès concurrentiel ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) et un objet `critical_section` pour calculer le nombre de nombres premiers dans un objet [std :: Array](../../standard-library/array-class-stl.md) . Cet exemple n'évolue pas car chaque thread doit attendre d'accéder à la variable partagée `prime_sum`.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

Cet exemple peut également entraîner une baisse des performances car l'opération de verrouillage fréquente sérialise efficacement la boucle. De plus, quand un objet de runtime d'accès concurrentiel effectue une opération de blocage, le planificateur peut créer un thread supplémentaire pour effectuer un autre travail pendant que le premier thread attend des données. Si le runtime crée de nombreux threads car de nombreuses tâches attendent des données partagées, l'application peut fonctionner difficilement ou entrer dans un état de ressources insuffisantes.

La bibliothèque de modèles parallèles définit la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) , qui vous permet d’éliminer l’état partagé en fournissant un accès à des ressources partagées sans verrou. La classe `combinable` fournit un stockage local des threads qui vous permet d’effectuer des calculs affinés, puis de fusionner ces calculs dans un résultat final. Vous pouvez considérer un objet `combinable` comme une variable de réduction.

L'exemple suivant modifie le précédent en utilisant un objet `combinable` au lieu d'un objet `critical_section` pour calculer la somme. Cet exemple évolue car chaque thread retient sa propre copie locale de la somme. Cet exemple utilise la méthode [Concurrency :: combinable :: combine](reference/combinable-class.md#combine) pour fusionner les calculs locaux dans le résultat final.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Pour obtenir la version complète de cet exemple, consultez [Comment : utiliser combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Pour plus d’informations sur la classe `combinable`, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

[[Haut](#top)]

## <a name="false-sharing"></a>Dans la mesure du possible, évitez le faux partage

Le *faux partage* se produit lorsque plusieurs tâches simultanées exécutées sur des processeurs distincts écrivent dans des variables situées sur la même ligne de cache. Quand une seule tâche écrit dans l’une des variables, la ligne de cache des deux variables est invalidée. Chaque processeur doit recharger la ligne de cache à chaque fois que la ligne de cache est invalidée. Ainsi, le faux partage peut diminuer les performances dans votre application.

L’exemple de base suivant illustre deux tâches simultanées qui incrémente chacune une variable de compteur partagée.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Pour éliminer le partage des données entre les deux tâches, vous pouvez modifier l’exemple pour utiliser deux variables de compteur. Cet exemple calcule la valeur de compteur finale une fois que les tâches sont terminées. Toutefois, cet exemple illustre le faux partage car les variables `count1` et `count2` sont susceptibles de se trouver sur la même ligne de cache.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Un moyen de supprimer le faux partage consiste à s'assurer que les variables de compteur sont sur des lignes de cache distinctes. L'exemple suivant aligne les variables `count1` et `count2` sur des limites de 64 octets.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

Cet exemple suppose que la taille du cache en mémoire s'élève à 64 octets ou moins.

Nous vous recommandons d’utiliser la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) quand vous devez partager des données entre des tâches. La classe `combinable` crée des variables locales des thread de manière à ce que le faux partage soit moins probable. Pour plus d’informations sur la classe `combinable`, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

[[Haut](#top)]

## <a name="lifetime"></a>S’assurer que les variables sont valides pendant toute la durée de vie d’une tâche

Quand vous fournissez une expression lambda à un groupe de tâches ou à un algorithme parallèle, la clause de capture spécifie si le corps de l’expression lambda accède aux variables dans la portée englobante par valeur ou par référence. Quand vous passez des variables à une expression lambda par référence, vous devez vous assurer que la durée de vie de cette variable persiste jusqu'à ce que la tâche se termine.

Prenons l'exemple suivant qui définit la classe `object` et la fonction `perform_action`. La fonction `perform_action` crée une variable `object` et effectue une action sur cette variable de façon asynchrone. Étant donné que la fin de la tâche n'est pas garantie avant le retour de la fonction `perform_action`, le programme se bloque ou adopte un comportement non spécifié si la variable `object` est détruite quand la tâche est en cours d'exécution.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

Selon les besoins de votre application, vous pouvez utiliser une des techniques suivantes pour garantir la validité des variables pendant toute la durée de chaque tâche.

L'exemple suivant passe la variable `object` par valeur à la tâche. Par conséquent, la tâche s’exécute sur sa propre copie de la variable.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Étant donné que la variable `object` est passée par valeur, toute modification d'état qui se produit pour cette variable n'apparaît pas dans la copie d'origine.

L’exemple suivant utilise la méthode [Concurrency :: task_group :: wait](reference/task-group-class.md#wait) pour s’assurer que la tâche se termine avant le retour de la fonction `perform_action`.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Étant donné que la tâche se termine désormais avant le retour de la fonction, la fonction `perform_action` ne se comporte plus de façon asynchrone.

L'exemple suivant modifie la fonction `perform_action` pour prendre une référence à la variable `object`. L’appelant doit garantir que la durée de vie de la variable `object` est valide jusqu’à ce que la tâche se termine.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Vous pouvez également utiliser un pointeur pour contrôler la durée de vie d'un objet que vous passez à un groupe de tâches ou à un algorithme parallèle.

Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Bonnes pratiques sur le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Guide pratique pour utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[Guide pratique pour utiliser l’annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[Bonnes pratiques pour la bibliothèque d’agents asynchrones](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[Bonnes pratiques en général du runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
