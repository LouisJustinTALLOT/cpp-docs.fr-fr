---
title: Parallélisme des tâches (runtime d’accès concurrentiel)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: c9f18dfd1498538ce3700fd73a27ce6f6088ee42
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331215"
---
# <a name="task-parallelism-concurrency-runtime"></a>Parallélisme des tâches (runtime d’accès concurrentiel)

Dans le Runtime d’accès concurrentiel, un *tâche* est une unité de travail qui exécute un travail spécifique et s’exécute généralement en parallèle avec d’autres tâches. Une tâche peut être décomposée en tâches supplémentaires plus affinées qui sont organisées en un *groupe de tâches*.

Vous utilisez des tâches quand vous écrivez du code asynchrone et que vous voulez qu’une opération se produise une fois que l’opération asynchrone est terminée. Par exemple, vous pouvez utiliser une tâche pour lire de façon asynchrone à partir d’un fichier, puis utiliser une autre tâche, un *tâche de continuation*, qui est expliqué plus loin dans ce document, pour traiter les données dès qu’il est disponible. À l’inverse, vous pouvez utiliser des groupes de tâches pour décomposer un travail parallèle en éléments plus petits. Par exemple, supposons que vous ayez un algorithme récursif qui divise le travail restant en deux partitions. Vous pouvez utiliser des groupes de tâches pour exécuter ces partitions simultanément, puis attendre que le travail divisé soit terminé.

> [!TIP]
> Lorsque vous souhaitez appliquer la même routine à chaque élément d’une collection en parallèle, utilisez un algorithme parallèle, tel que [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), au lieu d’une tâche ou un groupe de tâches. Pour plus d’informations sur les algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Points clés

- Quand vous passez des variables à une expression lambda par référence, vous devez vous assurer que la durée de vie de cette variable persiste jusqu’à ce que la tâche se termine.

- Utiliser des tâches (la [concurrency::task](../../parallel/concrt/reference/task-class.md) classe) lorsque vous écrivez du code asynchrone. La classe task utilise le pool de threads Windows en tant que planificateur, et non le runtime d’accès concurrentiel.

- Utiliser des groupes de tâches (la [concurrency::task_group](reference/task-group-class.md) classe ou le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme) lorsque vous voulez décomposer le travail parallèle en éléments plus petits et attendez que les plus petits éléments à terminer.

- Utilisez le [Concurrency::Task :: Then](reference/task-class.md#then) méthode pour créer des continuations. Un *continuation* est une tâche qui s’exécute de façon asynchrone après une autre tâche se termine. Vous pouvez connecter autant de continuations que vous voulez pour former une chaîne de travail asynchrone.

- Une continuation basée sur des tâches est toujours planifiée pour l’exécution quand la tâche antécédente se termine, même quand la tâche antécédente est annulée ou lève une exception.

- Utilisez [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) pour créer une tâche qui se termine une fois que chaque membre d’un ensemble de tâches se termine. Utilisez [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) pour créer une tâche qui se termine après un membre d’un ensemble de tâches se termine.

- Les tâches et les groupes de tâches peuvent participer au mécanisme d’annulation de la bibliothèque de modèles parallèles (PPL). Pour plus d’informations, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

- Pour savoir comment le runtime gère les exceptions levées par des tâches et des groupes de tâches, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>Dans ce document

- [Utilisation d’Expressions Lambda](#lambdas)

- [La classe de tâche](#task-class)

- [Tâches de continuation](#continuations)

- [Sur la valeur et les Continuations basées sur des tâches](#value-versus-task)

- [Composition des tâches](#composing-tasks)

    - [Fonction when_all](#when-all)

    - [Fonction when_any](#when-any)

- [Exécution de la tâche différée](#delayed-tasks)

- [Groupes de tâches](#task-groups)

- [Comparaison de task_group à structured_task_group](#comparing-groups)

- [Exemple](#example)

- [Programmation fiable](#robust)

##  <a name="lambdas"></a> Utilisation d’Expressions Lambda

En raison de leur syntaxe concise, les expressions lambda constituent une manière courante de définir le travail effectué par les tâches et les groupes de tâches. Voici quelques conseils d'utilisation :

- Étant donné que les tâches s'exécutent généralement sur des threads d'arrière-plan, tenez compte de la durée de vie des objets quand vous capturez des variables dans des expressions lambda. Quand vous capturez une variable par valeur, une copie de cette variable est effectuée dans le corps de l'expression lambda. Quand vous capturez par référence, aucune copie n'est effectuée. Par conséquent, vérifiez que la durée de vie d'une variable que vous capturez par référence est supérieure à celle de la tâche qui l'utilise.

- Quand vous passez une expression lambda à une tâche, ne capturez pas de variables allouées sur la pile par référence.

- Soyez explicite sur les variables capturées dans les expressions lambda pour pouvoir identifier ce que vous capturez par valeur ou par référence. C'est pour cela que nous vous recommandons de ne pas utiliser les options `[=]` ou `[&]` pour les expressions lambda.

Il est courant qu'une seule tâche dans une chaîne de continuation s'assigne à une variable et qu'une autre tâche lise cette variable. Vous ne pouvez pas capturer par valeur car chaque tâche de continuation contiendrait alors une copie différente de la variable. Pour les variables allouées par la pile, vous ne pouvez pas non plus capturer par référence car la variable n'est plus être plus valide.

Pour résoudre ce problème, utilisez un pointeur intelligent, telles que [std::shared_ptr](../../standard-library/shared-ptr-class.md), pour encapsuler la variable et passer le pointeur intelligent par valeur. Ainsi, l’objet sous-jacent peut être assigné et lu, et il survit aux tâches qui l’utilisent. Utilisez cette technique, même quand la variable est un pointeur ou un handle compté par référence (`^`) à un objet Windows Runtime. Voici un exemple de base :

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../cpp/lambda-expressions-in-cpp.md).

##  <a name="task-class"></a> La classe de tâche

Vous pouvez utiliser la [concurrency::task](../../parallel/concrt/reference/task-class.md) classe pour composer des tâches dans un ensemble d’opérations dépendantes. Ce modèle de composition est pris en charge par la notion de *continuations*. Un continuation permet le code à exécuter lorsque le précédent, ou *antécédent*, tâche se termine. Le résultat de la tâche antécédente est transmis comme entrée à une ou plusieurs tâches de continuation. Quand une tâche antécédente est terminée, toutes les tâches de continuation qui l'attendent sont planifiées pour l'exécution. Chaque tâche de continuation reçoit une copie du résultat de la tâche antécédente. À leur tour, ces tâches de continuation peuvent également être des tâches antécédentes pour d’autres continuations, créant ainsi une chaîne de tâches. Les continuations vous aident à créer des chaînes de longueur arbitraire de tâches qui ont des dépendances spécifiques entre elles. De plus, une tâche peut participer à l’annulation avant le démarrage d’une tâche ou de manière coopérative pendant son exécution. Pour plus d’informations sur ce modèle d’annulation, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

`task` est une classe de modèle. Le paramètre de type `T` est le type du résultat produit par la tâche. Ce type peut être `void` si la tâche ne retourne pas de valeur. `T` ne peut pas utiliser le modificateur `const`.

Lorsque vous créez une tâche, vous fournissez un *fonction de travail* qui effectue le corps de la tâche. Cette fonction de travail se présente sous la forme d'une fonction lambda, de pointeur de fonction ou d'objet de fonction. Pour attendre une tâche se termine sans obtention du résultat, appelez le [Concurrency::Task :: wait](reference/task-class.md#wait) (méthode). Le `task::wait` méthode retourne un [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) valeur qui décrit si la tâche a été terminée ou annulée. Pour obtenir le résultat de la tâche, appelez le [Concurrency::Task :: Get](reference/task-class.md#get) (méthode). Cette méthode appelle `task::wait` pour attendre que la tâche se termine, et bloque donc l’exécution du thread actuel jusqu’à ce que le résultat soit disponible.

L'exemple suivant montre comment créer une tâche, attendre son résultat et afficher sa valeur. Les exemples fournis dans cette documentation utilisent des fonctions lambda car ils fournissent une syntaxe plus concise. Toutefois, vous pouvez également utiliser des pointeurs de fonction et des objets de fonction quand vous utilisez des tâches.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Lorsque vous utilisez le [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) (fonction), vous pouvez utiliser le `auto` mot clé au lieu de déclarer le type. Par exemple, prenons ce code qui crée et imprime la matrice d'identité :

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Vous pouvez utiliser la fonction `create_task` pour créer l'opération équivalente.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Si une exception est levée pendant l’exécution d’une tâche, le runtime marshale cette exception dans l’appel suivant à `task::get` ou `task::wait`, ou à une continuation basée sur la tâche. Pour plus d’informations sur le mécanisme de gestion des exceptions de tâche, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pour obtenir un exemple qui utilise `task`, [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), l’annulation, consultez [procédure pas à pas : connexion à l’aide de tâches et les requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (La classe `task_completion_event` est décrite ultérieurement dans ce document.)

> [!TIP]
>  Pour plus d’informations qui sont spécifiques aux tâches dans les applications UWP, consultez [programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) et [création d’opérations asynchrones en C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

##  <a name="continuations"></a> Tâches de continuation

En programmation asynchrone, il est très courant pour une opération asynchrone, une fois terminée, d'appeler une deuxième opération et de lui passer des données. Pour cela, il est d'usage d'avoir recours à des méthodes de rappel. Dans le Runtime d’accès concurrentiel, la même fonctionnalité est fournie par *tâches de continuation*. Une tâche de continuation (également appelée continuation) est une tâche asynchrone appelée par une autre tâche, qui est appelée le *antécédent*, lorsque l’antécédent est terminée. En utilisant les continuations, vous pouvez :

- passer des données de l'antécédent à la continuation ;

- spécifier les conditions précises dans lesquelles la continuation doit être ou non ;

- annuler une continuation avant son démarrage ou pendant son exécution de manière coopérative ;

- fournir des conseils sur la manière de planifier la continuation ; (Cela s’applique aux applications Universal Windows Platform (UWP) uniquement. Pour plus d’informations, consultez [création d’opérations asynchrones en C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- appeler plusieurs continuations depuis le même antécédent ;

- appeler une continuation quand certains ou tous les antécédents se terminent ;

- chaîner des continuations les unes à la suite des autres qu'elle qu'en soit la longueur ;

- utiliser une continuation pour gérer des exceptions levées par l'antécédent.

Ces fonctionnalités vous permettent d'exécuter une ou plusieurs tâches quand la première tâche se termine. Par exemple, vous pouvez créer une continuation qui compresse un fichier une fois que la première tâche le lit à partir du disque.

L’exemple suivant modifie le précédent pour utiliser le [Concurrency::Task :: Then](reference/task-class.md#then) méthode pour planifier une continuation qui imprime la valeur de la tâche antécédente lorsqu’il est disponible.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Vous pouvez chaîner et imbriquer des tâches jusqu’à n’importe quelle longueur. Une tâche peut également avoir plusieurs continuations. L’exemple suivant illustre une chaîne de continuation de base qui incrémente la valeur de la tâche précédente trois fois.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Une continuation peut également retourner une autre tâche. En l’absence d’annulation, cette tâche est exécutée avant la continuation suivante. Cette technique est appelée *désencapsulage asynchrone*. Le désencapsulage asynchrone s’avère utile quand vous voulez effectuer du travail supplémentaire en arrière-plan, mais sans que la tâche en cours bloque le thread actuel. (Cela est courant dans les applications UWP, où les continuations peuvent s’exécuter sur le thread d’interface utilisateur). L’exemple suivant montre trois tâches. La première tâche retourne une autre tâche qui est exécutée avant une tâche de continuation.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
>  Quand une continuation d’une tâche retourne une tâche imbriquée de type `N`, la tâche qui en résulte a le type `N`, et non `task<N>`, et elle se termine quand la tâche imbriquée se termine. En d’autres termes, la continuation désencapsule la tâche imbriquée.

##  <a name="value-versus-task"></a> Sur la valeur et les Continuations basées sur des tâches

Étant donné un objet `task` dont le type de retour est `T`, vous pouvez fournir une valeur de type `T` ou `task<T>` à ses tâches de continuation. Une continuation qui prend le type `T` est appelé un *continuation basée sur la valeur*. Une continuation basée sur des valeurs est planifiée pour l’exécution quand la tâche antécédente se termine sans erreur et qu’elle n’est pas annulée. Une continuation qui prend le type `task<T>` comme son paramètre est appelé un *basé sur des tâches de continuation*. Une continuation basée sur des tâches est toujours planifiée pour l’exécution quand la tâche antécédente se termine, même quand la tâche antécédente est annulée ou lève une exception. Vous pouvez alors appeler `task::get` pour obtenir le résultat de la tâche antécédente. Si la tâche antécédente a été annulée, `task::get` lève [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Si la tâche antécédente a levé une exception, `task::get` lève à nouveau cette exception. Une continuation basée sur des tâches n’est pas marquée comme annulée quand sa tâche antécédente est annulée.

##  <a name="composing-tasks"></a> Composition des tâches

Cette section décrit la [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) et [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) fonctions qui peuvent vous aider à composent plusieurs tâches pour implémenter des modèles courants.

###  <a name="when-all"></a> Fonction when_all

La fonction `when_all` produit une tâche qui s’exécute une fois qu’un ensemble de tâches est terminé. Cette fonction retourne un std ::[vecteur](../../standard-library/vector-class.md) objet qui contient le résultat de chaque tâche dans le jeu. L’exemple de base suivant utilise `when_all` pour créer une tâche qui représente l’achèvement de trois autres tâches.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
>  Les tâches que vous passez à `when_all` doivent être uniformes. En d'autres termes, elles doivent toutes retourner le même type.

Vous pouvez également utiliser la syntaxe `&&` pour produire une tâche qui s’exécute une fois qu’un ensemble de tâches est terminé, comme illustré dans l’exemple suivant.

`auto t = t1 && t2; // same as when_all`

Il est courant d’utiliser une continuation avec `when_all` pour exécuter une action une fois qu’un ensemble de tâches est terminé. L’exemple suivant modifie le précédent pour imprimer la somme des trois tâches qui produisent chacune un résultat `int`.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

Dans cet exemple, vous pouvez également spécifier `task<vector<int>>` pour produire une continuation basée sur des tâches.

Si une tâche d'un ensemble de tâches est annulée ou lève une exception, `when_all` se termine immédiatement et n'attend pas que les tâches restantes se terminent. Si une exception est levée, le runtime lève à nouveau l'exception quand vous appelez `task::get` ou `task::wait` sur l'objet de tâche que `when_all` retourne. Si plusieurs tâches lèvent une exception, le runtime en choisit une. Par conséquent, vérifiez que vous observez toutes les exceptions une fois toutes les tâches terminées ; une exception de tâche non gérée entraîne l'arrêt de l'application.

Voici une fonction utilitaire que vous pouvez utiliser pour vous assurer que votre programme observe toutes les exceptions. Pour chaque tâche incluse dans la plage fournie, `observe_all_exceptions` déclenche toute exception qui s’est produite pour être à nouveau levée, puis avale cette exception.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Considérez une application UWP qui utilise C++ et XAML et écrit un ensemble de fichiers sur le disque. L'exemple suivant montre comment utiliser `when_all` et `observe_all_exceptions` pour vous assurer que le programme observe toutes les exceptions.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Pour exécuter cet exemple

1. Dans MainPage.xaml, ajoutez un contrôle `Button`.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. Dans MainPage.xaml.h, ajoutez ces déclarations anticipées à la section `private` de la déclaration de classe `MainPage`.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. Dans MainPage.xaml.cpp, implémentez le gestionnaire d'événements `Button_Click`.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. Dans MainPage.xaml.cpp, implémentez `WriteFilesAsync` comme indiqué dans l'exemple.

> [!TIP]
> `when_all` est une fonction non bloquante qui produit un `task` en tant que résultat. Contrairement aux [task::wait](reference/task-class.md#wait), il est déconseillé d’appeler cette fonction dans une application UWP sur le thread ASTA (Application STA).

###  <a name="when-any"></a> Fonction when_any

La fonction `when_any` produit une tâche qui se termine quand la première tâche d’un ensemble de tâches se termine. Cette fonction retourne un [std::pair](../../standard-library/pair-structure.md) objet qui contient le résultat de la tâche achevée et l’index de cette tâche dans le jeu.

La fonction `when_any` s'avère particulièrement utile dans les scénarios suivants :

- Opérations redondantes. Considérez un algorithme ou une opération pouvant être exécutée plusieurs façons. Vous pouvez utiliser la fonction `when_any` pour sélectionner l'opération qui se termine en premier et annuler les opérations restantes.

- Opérations entrelacées. Vous pouvez démarrer plusieurs opérations qui doivent toutes se terminer et utiliser la fonction `when_any` pour traiter les résultats à mesure que chaque opération se termine. Lorsqu’une opération se termine, vous pouvez démarrer une ou plusieurs autres tâches.

- Opérations limitées. Vous pouvez utiliser la fonction `when_any` pour étendre le scénario précédent en limitant le nombre d'opérations simultanées.

- Opérations expirées. Vous pouvez utiliser la fonction `when_any` pour choisir une ou plusieurs tâches et une tâche qui se termine après un délai spécifique.

Comme avec `when_all`, il est courant d'utiliser une continuation avec `when_any` pour effectuer une action quand la première tâche d'un ensemble de tâches se termine. L’exemple de base suivant utilise `when_any` pour créer une tâche qui se termine quand la première des trois autres tâches se termine.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

Dans cet exemple, vous pouvez également spécifier `task<pair<int, size_t>>` pour produire une continuation basée sur des tâches.

> [!NOTE]
> Comme avec `when_all`, les tâches que vous passez à `when_any` doivent toutes retourner le même type.

Vous pouvez également utiliser la syntaxe `||` pour produire une tâche qui s’exécute une fois que la première tâche d’un ensemble de tâches est terminée, comme illustré dans l’exemple suivant.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Comme avec `when_all`, `when_any` est non bloquant et peut être appelé dans une application UWP sur le thread ASTA.

##  <a name="delayed-tasks"></a> Exécution de la tâche différée

Il est parfois nécessaire de retarder l’exécution d’une tâche jusqu’à ce qu’une condition soit satisfaite, ou de démarrer une tâche en réponse à un événement externe. Par exemple, en programmation asynchrone, vous devrez peut-être démarrer une tâche en réponse à un événement d'achèvement d'E/S.

Deux façons de procéder pour cela consistent à utiliser une continuation ou à démarrer une tâche et attendre un événement au sein de la fonction de travail de la tâche. Toutefois, il existe des cas où il n'est pas possible d'utiliser l'une de ces techniques. Par exemple, pour créer une continuation, vous devez disposer de la tâche antécédente. Toutefois, si vous n’avez pas de l’antécédent de tâche, vous pouvez créer un *événement d’achèvement de tâche* et chaîner ultérieurement cet événement d’achèvement à la tâche antécédente lorsqu’elle est disponible. De plus, puisqu’une tâche en attente bloque également un thread, vous pouvez utiliser des événements d’achèvement de tâche pour effectuer un travail quand une opération asynchrone se termine et ainsi libérer un thread.

Le [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) classe permet de simplifier cette composition de tâches. Comme la classe `task`, le paramètre de type `T` est le type du résultat produit par la tâche. Ce type peut être `void` si la tâche ne retourne pas de valeur. `T` ne peut pas utiliser le modificateur `const`. En règle générale, un objet `task_completion_event` est fourni à un thread ou une tâche qui le signale quand sa valeur devient disponible. En même temps, une ou plusieurs tâches sont définies en tant qu'écouteurs de cet événement. Quand l’événement est défini, les tâches de l’écouteur s’achèvent et leurs continuations sont planifiées pour s’exécuter.

Pour obtenir un exemple qui utilise `task_completion_event` pour implémenter une tâche qui se termine après un certain délai, consultez [Comment : créer une tâche qui se termine après un délai](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

##  <a name="task-groups"></a> Groupes de tâches

Un *groupe de tâches* organise une collection de tâches. Les groupes de tâches transmettent des tâches vers une file d’attente de vol de travail. Le planificateur supprime les tâches de cette file d'attente et les exécute sur les ressources informatiques disponibles. Après avoir ajouté des tâches à un groupe de tâches, vous pouvez attendre que toutes les tâches se terminent ou annuler celles qui n’ont pas encore commencé.

La bibliothèque PPL utilise le [concurrency::task_group](reference/task-group-class.md) et [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) classes pour représenter des groupes de tâches et le [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) classe pour représenter les tâches qui s’exécutent dans ces groupes. La classe `task_handle` encapsule le code qui effectue le travail. Comme la classe `task`, la fonction de travail se présente sous la forme d'une fonction lambda, de pointeur de fonction ou d'objet de fonction. En général, vous n'avez pas besoin d'utiliser directement des objets `task_handle`. Au lieu de cela, vous passez des fonctions de travail à un groupe de tâches et celui-ci crée et gère les objets `task_handle`.

La bibliothèque PPL divise les groupes de tâches en deux catégories : *groupes de tâches non structurés* et *structurées de groupes de tâches*. La bibliothèque de modèles parallèles utilise la classe `task_group` pour représenter les groupes de tâches non structurés et la classe `structured_task_group` pour représenter les groupes de tâches structurés.

> [!IMPORTANT]
> La bibliothèque PPL définit également la [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme, qui utilise le `structured_task_group` classe pour exécuter un ensemble de tâches en parallèle. Étant donné que l'algorithme `parallel_invoke` a une syntaxe plus concise, nous vous recommandons de l'utiliser à la place de la classe `structured_task_group` dès que possible. La rubrique [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md) décrit `parallel_invoke` plus en détail.

Utilisez `parallel_invoke` quand vous avez plusieurs tâches indépendantes à exécuter en même temps, et que vous devez attendre que toutes les tâches soient terminées avant de continuer. Cette technique est souvent appelée *bifurcation et jointure* parallélisme. Utilisez `task_group` quand vous avez plusieurs tâches indépendantes à exécuter en même temps, mais que vous voulez attendre plus tard que les tâches se terminent. Par exemple, vous pouvez ajouter des tâches à un objet `task_group` et attendre qu'elles se terminent dans une autre fonction ou à partir d'un autre thread.

Les groupes de tâches prennent en charge le concept d'annulation. L'annulation vous permet de signaler à toutes les tâches actives que vous voulez annuler l'opération globale. L’annulation empêche également les tâches qui n’ont pas encore démarré de démarrer. Pour plus d’informations sur l’annulation, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

Le runtime fournit également un modèle de gestion des exceptions qui vous permet de lever une exception à partir d’une tâche et de gérer cette exception quand vous attendez que le groupe de tâches associé se termine. Pour plus d’informations sur ce modèle de gestion des exceptions, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

##  <a name="comparing-groups"></a> Comparaison de task_group à structured_task_group

Bien que nous vous recommandions d’utiliser `task_group` ou `parallel_invoke` au lieu de la classe `structured_task_group`, dans certains cas, vous pouvez utiliser `structured_task_group`, par exemple, quand vous écrivez un algorithme parallèle qui effectue un nombre variable de tâches ou qui requiert la prise en charge de l’annulation. Cette section explique les différences entre les classes `task_group` et `structured_task_group`.

La classe `task_group` est thread-safe. Ainsi, vous pouvez ajouter des tâches à un objet `task_group` à partir de plusieurs threads et attendre ou annuler un objet `task_group` à partir de plusieurs threads. La construction et la destruction d'un objet `structured_task_group` doit se produire dans la même portée lexicale. De plus, toutes les opérations sur un objet `structured_task_group` doivent se produire sur le même thread. L’exception à cette règle est la [Concurrency::structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) et [Concurrency::structured_task_group :: is_canceling](reference/structured-task-group-class.md#is_canceling) méthodes. Une tâche enfant peut appeler ces méthodes pour annuler le groupe de tâches parent ou vérifier l’annulation à tout moment.

Vous pouvez exécuter des tâches supplémentaires sur un `task_group` objet une fois que vous appelez le [Concurrency::task_group :: wait](reference/task-group-class.md#wait) ou [Concurrency::task_group :: run_and_wait](reference/task-group-class.md#run_and_wait) (méthode). À l’inverse, si vous exécutez des tâches supplémentaires sur un `structured_task_group` objet une fois que vous appelez le [Concurrency::structured_task_group :: wait](reference/structured-task-group-class.md#wait) ou [Concurrency::structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait) méthodes , puis le comportement est indéfini.

Étant donné que la classe `structured_task_group` n’est pas synchronisée entre les threads, elle a moins de charge d’exécution que la classe `task_group`. Par conséquent, si votre problème ne requiert pas de planification du travail à partir de plusieurs threads et que vous ne pouvez pas utiliser l'algorithme `parallel_invoke`, la classe `structured_task_group` peut vous aider à écrire du code plus performant.

Si vous utilisez un seul objet `structured_task_group` à l'intérieur d'un autre objet `structured_task_group`, l'objet interne doit se terminer et être détruit avant la fin de l'objet externe. La classe `task_group` ne requiert pas que des groupes de tâches imbriqués se terminent avant les groupes externes.

Les groupes de tâches non structurés et les groupes de tâches structurés utilisent différemment les handles de tâches. Vous pouvez passer directement des fonctions de travail à un objet `task_group` ; l'objet `task_group` crée et gère le handle de tâche pour vous. La classe `structured_task_group` vous oblige à gérer un objet `task_handle` pour chaque tâche. Chaque objet `task_handle` doit rester valide pendant toute la durée de vie de son objet `structured_task_group` associé. Utilisez le [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) fonction permettant de créer un `task_handle` de l’objet, comme indiqué dans l’exemple de base suivant :

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Pour gérer les handles de tâches pour les cas où vous avez un nombre variable de tâches, utilisez une routine d’allocation de pile comme [_malloca](../../c-runtime-library/reference/malloca.md) ou une classe de conteneur, telles que std ::[vecteur](../../standard-library/vector-class.md).

`task_group` et `structured_task_group` prennent en charge l'annulation. Pour plus d’informations sur l’annulation, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

##  <a name="example"></a> Exemple

L’exemple de base suivant montre comment utiliser des groupes de tâches. Cet exemple utilise l'algorithme `parallel_invoke` pour effectuer deux tâches simultanément. Chaque tâche ajoute des sous-tâches à un objet `task_group`. Notez que la classe `task_group` permet à plusieurs tâches d’y ajouter des tâches simultanément.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Voici un exemple de sortie pour cet exemple :

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Étant donné que l’algorithme `parallel_invoke` exécute des tâches simultanément, l’ordre des messages de sortie peut varier.

Pour obtenir des exemples complets qui montrent comment utiliser le `parallel_invoke` algorithme, consultez [Comment : utiliser parallel_invoke pour écrire une Routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) et [Comment : utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Pour obtenir un exemple complet qui utilise le `task_group` classe pour implémenter des tâches asynchrones futures, consultez [procédure pas à pas : implémentation de tâches Futures](../../parallel/concrt/walkthrough-implementing-futures.md).

##  <a name="robust"></a> Programmation fiable

Assurez-vous de bien comprendre le rôle de l’annulation et la gestion des exceptions quand vous utilisez des tâches, des groupes de tâches et des algorithmes parallèles. Par exemple, dans une arborescence de travail parallèle, une tâche qui est annulée empêche les tâches enfants de s'exécuter. Des problèmes peuvent alors survenir si l’une des tâches enfants effectue une opération importante pour votre application, comme la libération d’une ressource. De plus, si une tâche enfant lève une exception, cette exception risque de se propager via un destructeur d’objet et d’entraîner un comportement indéfini dans votre application. Pour obtenir un exemple qui illustre ces points, consultez le [comprendre comment l’annulation et Exception gestion affectent la Destruction d’objets](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) section dans les meilleures pratiques dans le document de la bibliothèque de modèles parallèles. Pour plus d’informations sur l’annulation et les modèles de gestion des exceptions dans la bibliothèque PPL, consultez [l’annulation](../../parallel/concrt/cancellation-in-the-ppl.md) et [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Guide pratique pour utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances de l'algorithme de tri bitonique.|
|[Guide pratique pour utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances d'un programme qui effectue plusieurs opérations sur une source de données partagée.|
|[Guide pratique pour créer une tâche qui se termine après un certain délai](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Montre comment utiliser le `task`, `cancellation_token_source`, `cancellation_token`, et `task_completion_event` classes pour créer une tâche qui se termine après un certain délai.|
|[Procédure pas à pas : implémentation d’objets future](../../parallel/concrt/walkthrough-implementing-futures.md)|Montre comment combiner les fonctionnalités existantes du runtime d'accès concurrentiel pour en optimiser l'usage.|
|[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Décrit la bibliothèque de modèles parallèles (PPL), qui fournit un modèle de programmation impérative pour développer des applications simultanées.|

## <a name="reference"></a>Référence

[task (Concurrency Runtime), classe](../../parallel/concrt/reference/task-class.md)

[task_completion_event, classe](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all, fonction](reference/concurrency-namespace-functions.md#when_all)

[when_any, fonction](reference/concurrency-namespace-functions.md#when_any)

[task_group, classe](reference/task-group-class.md)

[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group, classe](../../parallel/concrt/reference/structured-task-group-class.md)
