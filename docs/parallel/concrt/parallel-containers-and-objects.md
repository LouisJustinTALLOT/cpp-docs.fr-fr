---
title: Conteneurs et objets parallèles
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: dffe9b3490f52645414643ebc23ab78553abafff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213903"
---
# <a name="parallel-containers-and-objects"></a>Conteneurs et objets parallèles

La bibliothèque de modèles parallèles (PPL) comprend plusieurs conteneurs et objets qui fournissent un accès thread-safe à leurs éléments.

Un *conteneur simultané* fournit un accès concurrentiel sécurisé aux opérations les plus importantes. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. La fonctionnalité de ces conteneurs ressemble à celles fournies par la bibliothèque standard C++. Par exemple, la classe [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) ressemble à la classe [std :: Vector](../../standard-library/vector-class.md) , sauf que la `concurrent_vector` classe vous permet d’ajouter des éléments en parallèle. Utilisez des conteneurs simultanés lorsque vous avez du code parallèle qui requiert un accès en lecture et en écriture au même conteneur.

Un *objet simultané* est partagé simultanément entre les composants. Un processus qui calcule l’état d’un objet simultané en parallèle produit le même résultat qu’un autre processus qui calcule le même État en série. La classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) est un exemple de type d’objet simultané. La `combinable` classe vous permet d’effectuer des calculs en parallèle, puis de combiner ces calculs dans un résultat final. Utilisez des objets simultanés quand vous utilisez un mécanisme de synchronisation, par exemple un mutex, pour synchroniser l’accès à une variable ou une ressource partagée.

## <a name="sections"></a><a name="top"></a>Sections

Cette rubrique décrit en détail les conteneurs et objets parallèles suivants.

Conteneurs simultanés :

- [Classe concurrent_vector](#vector)

  - [Différences entre concurrent_vector et Vector](#vector-differences)

  - [Opérations sécurisées pour l’accès concurrentiel](#vector-safety)

  - [Sécurité des exceptions](#vector-exceptions)

- [Classe concurrent_queue](#queue)

  - [Différences entre les concurrent_queue et la file d’attente](#queue-differences)

  - [Opérations sécurisées pour l’accès concurrentiel](#queue-safety)

  - [Prise en charge des itérateurs](#queue-iterators)

- [Classe concurrent_unordered_map](#unordered_map)

  - [Différences entre concurrent_unordered_map et unordered_map](#map-differences)

  - [Opérations sécurisées pour l’accès concurrentiel](#map-safety)

- [Classe concurrent_unordered_multimap](#unordered_multimap)

- [Classe concurrent_unordered_set](#unordered_set)

- [Classe concurrent_unordered_multiset](#unordered_multiset)

Objets simultanés :

- [combinable, classe](#combinable)

  - [Méthodes et fonctionnalités](#combinable-features)

  - [Exemples](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>Classe concurrent_vector

La classe [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) est une classe de conteneur de séquence qui, tout comme la classe [std :: Vector](../../standard-library/vector-class.md) , vous permet d’accéder de manière aléatoire à ses éléments. La `concurrent_vector` classe permet les opérations d’ajout et d’accès à l’élément sécurisées pour l’accès concurrentiel. Les opérations d’ajout n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de parcours sont également sécurisés pour la concurrence. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Différences entre concurrent_vector et Vector

La `concurrent_vector` classe ressemble étroitement à la `vector` classe. La complexité des opérations d’ajout, d’accès aux éléments et d’accès aux itérateurs sur un `concurrent_vector` objet est identique à celle d’un `vector` objet. Les points suivants illustrent où `concurrent_vector` diffère de `vector` :

- Les opérations d’ajout, d’accès aux éléments, d’accès aux itérateurs et de parcours des itérateurs sur un `concurrent_vector` objet sont sécurisées pour l’accès concurrentiel.

- Vous pouvez uniquement ajouter des éléments à la fin d’un `concurrent_vector` objet. La `concurrent_vector` classe ne fournit pas la `insert` méthode.

- Un `concurrent_vector` objet n’utilise pas la [sémantique de déplacement](../../cpp/rvalue-reference-declarator-amp-amp.md) lorsque vous l’ajoutez.

- La `concurrent_vector` classe ne fournit pas les `erase` `pop_back` méthodes ou. Comme avec `vector` , utilisez la méthode [Clear](reference/concurrent-vector-class.md#clear) pour supprimer tous les éléments d’un `concurrent_vector` objet.

- La `concurrent_vector` classe ne stocke pas ses éléments de façon contiguë en mémoire. Par conséquent, vous ne pouvez pas utiliser la `concurrent_vector` classe dans toutes les façons d’utiliser un tableau. Par exemple, pour une variable nommée `v` de type `concurrent_vector` , l’expression `&v[0]+2` produit un comportement indéfini.

- La `concurrent_vector` classe définit les méthodes [grow_by](reference/concurrent-vector-class.md#grow_by) et [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Ces méthodes ressemblent à la méthode [Resize](reference/concurrent-vector-class.md#resize) , sauf qu’elles sont sécurisées.

- Un `concurrent_vector` objet ne déplace pas ses éléments lorsque vous l’ajoutez ou le redimensionnez. Cela permet aux pointeurs et itérateurs existants de rester valides pendant les opérations simultanées.

- Le runtime ne définit pas une version spécialisée de `concurrent_vector` pour le type **`bool`** .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Opérations sécurisées pour l’accès concurrentiel

Toutes les méthodes qui ajoutent ou augmentent la taille d’un `concurrent_vector` objet, ou accèdent à un élément dans un `concurrent_vector` objet, sont sécurisées pour l’accès concurrentiel. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. L’exception à cette règle est la `resize` méthode.

Le tableau suivant répertorie les `concurrent_vector` méthodes et les opérateurs courants qui sont sécurisés pour l’accès concurrentiel.

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[commencer](reference/concurrent-vector-class.md#begin)|[frontal](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Précédent](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[maximale](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

Les opérations que le Runtime fournit pour la compatibilité avec la bibliothèque C++ standard, par exemple, `reserve` , ne sont pas sécurisées pour l’accès concurrentiel. Le tableau suivant répertorie les méthodes et les opérateurs courants qui ne sont pas sécurisés pour la simultanéité.

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[reserve](reference/concurrent-vector-class.md#reserve)|
|[clear](reference/concurrent-vector-class.md#clear)|[redimensionner](reference/concurrent-vector-class.md#resize)|
|[opérateur =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Les opérations qui modifient la valeur des éléments existants ne sont pas sécurisées pour l’accès concurrentiel. Utilisez un objet de synchronisation, tel qu’un objet [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) pour synchroniser les opérations de lecture et d’écriture simultanées avec le même élément de données. Pour plus d’informations sur les objets de synchronisation, consultez [structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md).

Lorsque vous convertissez du code existant qui utilise `vector` pour utiliser `concurrent_vector` , les opérations simultanées peuvent entraîner la modification du comportement de votre application. Par exemple, considérez le programme suivant qui effectue simultanément deux tâches sur un `concurrent_vector` objet. La première tâche ajoute des éléments supplémentaires à un `concurrent_vector` objet. La deuxième tâche calcule la somme de tous les éléments dans le même objet.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Bien que la `end` méthode soit de sécurité concurrentielle, un appel simultané à la méthode [push_back](reference/concurrent-vector-class.md#push_back) provoque la modification de la valeur retournée par `end` . Le nombre d’éléments que l’itérateur traverse est indéterminé. Par conséquent, ce programme peut produire un résultat différent chaque fois que vous l’exécutez. Lorsque le type d’élément n’est pas trivial, il est possible qu’une condition de concurrence existe entre `push_back` les `end` appels et. La `end` méthode peut retourner un élément qui est alloué, mais qui n’est pas complètement initialisé.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Sécurité des exceptions

Si une opération de croissance ou d’assignation lève une exception, l’état de l' `concurrent_vector` objet devient non valide. Le comportement d’un `concurrent_vector` objet qui est dans un État non valide n’est pas défini, sauf indication contraire. Toutefois, le destructeur libère toujours la mémoire que l’objet alloue, même si l’objet est dans un État non valide.

Le type de données des éléments vectoriels, `T` , doit remplir les conditions suivantes. Dans le cas contraire, le comportement de la `concurrent_vector` classe n’est pas défini.

- Le destructeur ne doit pas lever d’exception.

- Si le constructeur de copie ou par défaut lève, le destructeur ne doit pas être déclaré à l’aide du **`virtual`** mot clé et doit fonctionner correctement avec la mémoire initialisée à zéro.

[[Haut](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>Classe concurrent_queue

La classe [Concurrency :: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , tout comme la classe [std :: queue](../../standard-library/queue-class.md) , vous permet d’accéder à ses éléments d’avant et de retour. La classe permet d’effectuer des opérations de mise en file d’attente et de retrait de la file d’attente `concurrent_queue` sécurisées. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. La `concurrent_queue` classe fournit également une prise en charge d’itérateur qui n’est pas sécurisée pour la concurrence.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Différences entre les concurrent_queue et la file d’attente

La `concurrent_queue` classe ressemble étroitement à la `queue` classe. Les points suivants illustrent où `concurrent_queue` diffère de `queue` :

- Les opérations de mise en file d’attente et de retrait de la file d’attente sur un `concurrent_queue` objet sont sécurisées.

- La `concurrent_queue` classe fournit la prise en charge de l’itérateur qui n’est pas sécurisée pour l’accès concurrentiel.

- La `concurrent_queue` classe ne fournit pas les `front` `pop` méthodes ou. La `concurrent_queue` classe remplace ces méthodes en définissant la méthode [try_pop](reference/concurrent-queue-class.md#try_pop) .

- La `concurrent_queue` classe ne fournit pas la `back` méthode. Par conséquent, vous ne pouvez pas référencer la fin de la file d’attente.

- La `concurrent_queue` classe fournit la méthode [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) à la place de la `size` méthode. La `unsafe_size` méthode n’est pas sécurisée pour la concurrence.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Opérations sécurisées pour l’accès concurrentiel

Toutes les méthodes qui sont empilées ou déplacées de la file d’attente d’un `concurrent_queue` objet sont sécurisées pour l’accès concurrentiel. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

Le tableau suivant répertorie les `concurrent_queue` méthodes et les opérateurs courants qui sont sécurisés pour l’accès concurrentiel.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Bien que la `empty` méthode soit sécurisée pour l’accès concurrentiel, une opération simultanée peut provoquer l’augmentation ou la réduction de la file d’attente avant le retour de la `empty` méthode.

Le tableau suivant répertorie les méthodes et les opérateurs courants qui ne sont pas sécurisés pour la simultanéité.

|||
|-|-|
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Prise en charge des itérateurs

`concurrent_queue`Fournit des itérateurs qui ne sont pas sécurisés pour l’accès concurrentiel. Nous vous recommandons d’utiliser ces itérateurs uniquement pour le débogage.

Un `concurrent_queue` itérateur parcourt uniquement les éléments dans le sens avant. Le tableau suivant indique les opérateurs pris en charge par chaque itérateur.

|Opérateur|Description|
|--------------|-----------------|
|`operator++`|Avance jusqu’à l’élément suivant dans la file d’attente. Cet opérateur est surchargé pour fournir une sémantique pré-incrémentée et postérieure à l’incrémentation.|
|`operator*`|Récupère une référence à l’élément actuel.|
|`operator->`|Récupère un pointeur vers l’élément actuel.|

[[Haut](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>Classe concurrent_unordered_map

La classe [Concurrency :: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) est une classe de conteneur associatif qui, tout comme la classe [std :: unordered_map](../../standard-library/unordered-map-class.md) , contrôle une séquence de longueur variable d’éléments de type [std ::p air \<const Key, Ty> ](../../standard-library/pair-structure.md). Imaginez une carte non triée comme un dictionnaire auquel vous pouvez ajouter une paire clé/valeur ou rechercher une valeur par clé. Cette classe est utile lorsque vous avez plusieurs threads ou tâches qui doivent accéder simultanément à un conteneur partagé, les insérer ou les mettre à jour.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_map` . Cet exemple insère des touches de caractère dans la plage ['a', 'i']. Étant donné que l’ordre des opérations n’est pas déterminé, la valeur finale de chaque clé est également indéterminée. Toutefois, il est possible d’effectuer des insertions en parallèle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Pour obtenir un exemple qui utilise `concurrent_unordered_map` pour effectuer une opération de mappage et de réduction en parallèle, consultez [Comment : effectuer des opérations de mappage et de réduction en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Différences entre concurrent_unordered_map et unordered_map

La `concurrent_unordered_map` classe ressemble étroitement à la `unordered_map` classe. Les points suivants illustrent où `concurrent_unordered_map` diffère de `unordered_map` :

- Les `erase` méthodes,, `bucket` `bucket_count` et `bucket_size` sont nommées `unsafe_erase` , `unsafe_bucket` , `unsafe_bucket_count` et `unsafe_bucket_size` , respectivement. La `unsafe_` Convention d’affectation de noms indique que ces méthodes ne sont pas sécurisées pour l’accès concurrentiel. Pour plus d’informations sur la sécurité de l’accès concurrentiel, consultez [opérations sécurisées pour l’accès concurrentiel](#map-safety).

- Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants, ni ne modifient l’ordre des éléments qui existent déjà dans le mappage. Les opérations d’insertion et de parcours peuvent se produire simultanément.

- `concurrent_unordered_map`prend en charge uniquement l’itération vers l’avant.

- L’insertion n’invalide pas ou ne met pas à jour les itérateurs retournés par `equal_range` . L’insertion peut ajouter des éléments inégaux à la fin de la plage. L’itérateur de début pointe sur un élément égal.

Pour éviter les verrous mortels, aucune méthode de ne `concurrent_unordered_map` détient un verrou lorsqu’il appelle l’allocateur de mémoire, les fonctions de hachage ou tout autre code défini par l’utilisateur. En outre, vous devez vous assurer que la fonction de hachage évalue toujours les clés égales à la même valeur. Les meilleures fonctions de hachage distribuent uniformément les clés dans l’espace de code de hachage.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Opérations sécurisées pour l’accès concurrentiel

La `concurrent_unordered_map` classe permet d’effectuer des opérations d’insertion et d’accès aux éléments sécurisés pour l’accès concurrentiel. Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de parcours sont également sécurisés pour la concurrence. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. Le tableau suivant répertorie les `concurrent_unordered_map` méthodes et les opérateurs couramment utilisés qui sont sécurisés pour l’accès concurrentiel.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

Bien que la `count` méthode puisse être appelée en toute sécurité à partir de threads exécutés simultanément, différents threads peuvent recevoir des résultats différents si une nouvelle valeur est insérée simultanément dans le conteneur.

Le tableau suivant répertorie les méthodes et les opérateurs couramment utilisés qui ne sont pas sécurisés pour la simultanéité.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[opérateur =](reference/concurrent-unordered-map-class.md#operator_eq)

En plus de ces méthodes, toute méthode qui commence par `unsafe_` est également non sécurisée pour l’accès concurrentiel.

[[Haut](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>Classe concurrent_unordered_multimap

La classe [Concurrency :: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) ressemble étroitement à la `concurrent_unordered_map` classe, à ceci près qu’elle permet de mapper plusieurs valeurs à la même clé. Elle diffère également de `concurrent_unordered_map` selon les méthodes suivantes :

- La méthode [concurrent_unordered_multimap :: Insert](reference/concurrent-unordered-multimap-class.md#insert) retourne un itérateur au lieu de `std::pair<iterator, bool>` .

- La `concurrent_unordered_multimap` classe ne fournit pas `operator[]` ni la `at` méthode.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_multimap` . Cet exemple insère des touches de caractère dans la plage ['a', 'i']. `concurrent_unordered_multimap`permet à une clé d’avoir plusieurs valeurs.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Haut](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>Classe concurrent_unordered_set

La classe [Concurrency :: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) ressemble étroitement à la `concurrent_unordered_map` classe, à ceci près qu’elle gère des valeurs au lieu de paires clé/valeur. La `concurrent_unordered_set` classe ne fournit pas `operator[]` ni la `at` méthode.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_set` . Cet exemple insère des valeurs de caractère dans la plage ['a', 'i']. Il est possible d’effectuer des insertions en parallèle en toute sécurité.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Haut](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>Classe concurrent_unordered_multiset

La classe [Concurrency :: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) ressemble étroitement à la `concurrent_unordered_set` classe, à ceci près qu’elle autorise les valeurs dupliquées. Elle diffère également de `concurrent_unordered_set` selon les méthodes suivantes :

- La méthode [concurrent_unordered_multiset :: Insert](reference/concurrent-unordered-multiset-class.md#insert) retourne un itérateur au lieu de `std::pair<iterator, bool>` .

- La `concurrent_unordered_multiset` classe ne fournit pas `operator[]` ni la `at` méthode.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_multiset` . Cet exemple insère des valeurs de caractère dans la plage ['a', 'i']. `concurrent_unordered_multiset`permet à une valeur de se produire plusieurs fois.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Haut](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>combinable, classe

La classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) fournit un stockage local des threads réutilisable qui vous permet d’effectuer des calculs affinés, puis de fusionner ces calculs dans un résultat final. Vous pouvez considérer un objet `combinable` comme une variable de réduction.

La `combinable` classe est utile lorsque vous disposez d’une ressource qui est partagée entre plusieurs threads ou tâches. La `combinable` classe vous permet d’éliminer l’état partagé en fournissant un accès à des ressources partagées sans verrou. Par conséquent, cette classe fournit une alternative à l’utilisation d’un mécanisme de synchronisation, par exemple un mutex, pour synchroniser l’accès aux données partagées à partir de plusieurs threads.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente quelques-unes des méthodes importantes de la `combinable` classe. Pour plus d’informations sur toutes les `combinable` méthodes de classe, consultez [classe combinable](../../parallel/concrt/reference/combinable-class.md).

|Méthode|Description|
|------------|-----------------|
|[localisé](reference/combinable-class.md#local)|Récupère une référence à la variable locale associée au contexte de thread actuel.|
|[clear](reference/combinable-class.md#clear)|Supprime toutes les variables de thread local de l' `combinable` objet.|
|[Mixer](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Utilise la fonction combine fournie pour générer une valeur finale à partir de l’ensemble de tous les calculs locaux de thread.|

La `combinable` classe est une classe de modèle paramétrable sur le résultat final fusionné. Si vous appelez le constructeur par défaut, le `T` type de paramètre de modèle doit avoir un constructeur par défaut et un constructeur de copie. Si le `T` type de paramètre de modèle n’a pas de constructeur par défaut, appelez la version surchargée du constructeur qui prend une fonction d’initialisation comme paramètre.

Vous pouvez stocker des données supplémentaires dans un `combinable` objet après avoir appelé les méthodes [combine](reference/combinable-class.md#combine) ou [combine_each](reference/combinable-class.md#combine_each) . Vous pouvez également appeler les `combine` `combine_each` méthodes et plusieurs fois. Si aucune valeur locale dans un `combinable` objet n’est modifiée, les `combine` `combine_each` méthodes et produisent le même résultat chaque fois qu’elles sont appelées.

### <a name="examples"></a><a name="combinable-examples"></a> Exemples

Pour obtenir des exemples d’utilisation de la `combinable` classe, consultez les rubriques suivantes :

- [Comment : utiliser combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Comment : utiliser combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Haut](#top)]

## <a name="related-topics"></a>Rubriques connexes

[Comment : utiliser des conteneurs parallèles pour améliorer l’efficacité](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Montre comment utiliser des conteneurs parallèles pour stocker et accéder efficacement aux données en parallèle.

[Comment : utiliser combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Montre comment utiliser la `combinable` classe pour éliminer l’état partagé et ainsi améliorer les performances.

[Comment : utiliser combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Montre comment utiliser une `combine` fonction pour fusionner des jeux de données de thread local.

[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Décrit la bibliothèque PPL, qui fournit un modèle de programmation impératif qui favorise l’évolutivité et la facilité d’utilisation du développement d’applications simultanées.

## <a name="reference"></a>Informations de référence

[Classe concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)

[Classe concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)

[Classe concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[Classe concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[Classe concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[Classe concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable, classe](../../parallel/concrt/reference/combinable-class.md)
