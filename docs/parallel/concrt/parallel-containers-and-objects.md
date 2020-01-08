---
title: Conteneurs et objets parallèles
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: a2a44d267e16115f1b5a6ecb76308a66fc7abc8b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302300"
---
# <a name="parallel-containers-and-objects"></a>Conteneurs et objets parallèles

La bibliothèque de modèles parallèles (PPL) comprend plusieurs conteneurs et objets qui fournissent un accès thread-safe à leurs éléments.

Un *conteneur simultané* fournit un accès concurrentiel sécurisé aux opérations les plus importantes. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. La fonctionnalité de ces conteneurs ressemble à celles qui sont fournies par la C++ bibliothèque standard. Par exemple, la classe [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) ressemble à la classe [std :: Vector](../../standard-library/vector-class.md) , sauf que la classe `concurrent_vector` vous permet d’ajouter des éléments en parallèle. Utilisez des conteneurs simultanés lorsque vous avez du code parallèle qui requiert un accès en lecture et en écriture au même conteneur.

Un *objet simultané* est partagé simultanément entre les composants. Un processus qui calcule l’état d’un objet simultané en parallèle produit le même résultat qu’un autre processus qui calcule le même État en série. La classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) est un exemple de type d’objet simultané. La classe `combinable` vous permet d’effectuer des calculs en parallèle, puis de combiner ces calculs dans un résultat final. Utilisez des objets simultanés quand vous utilisez un mécanisme de synchronisation, par exemple un mutex, pour synchroniser l’accès à une variable ou une ressource partagée.

##  <a name="top"></a> Sections

Cette rubrique décrit en détail les conteneurs et objets parallèles suivants.

Conteneurs simultanés :

- [concurrent_vector, classe](#vector)

   - [Différences entre concurrent_vector et Vector](#vector-differences)

   - [Opérations sécurisées pour l’accès concurrentiel](#vector-safety)

   - [Sécurité des exceptions](#vector-exceptions)

- [concurrent_queue, classe](#queue)

   - [Différences entre les concurrent_queue et la file d’attente](#queue-differences)

   - [Opérations sécurisées pour l’accès concurrentiel](#queue-safety)

   - [Prise en charge des itérateurs](#queue-iterators)

- [concurrent_unordered_map, classe](#unordered_map)

   - [Différences entre concurrent_unordered_map et unordered_map](#map-differences)

   - [Opérations sécurisées pour l’accès concurrentiel](#map-safety)

- [concurrent_unordered_multimap, classe](#unordered_multimap)

- [concurrent_unordered_set, classe](#unordered_set)

- [concurrent_unordered_multiset, classe](#unordered_multiset)

Objets simultanés :

- [combinable, classe](#combinable)

   - [Méthodes et fonctionnalités](#combinable-features)

   - [Exemples](#combinable-examples)

##  <a name="vector"></a>Classe concurrent_vector

La classe [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) est une classe de conteneur de séquence qui, tout comme la classe [std :: Vector](../../standard-library/vector-class.md) , vous permet d’accéder de manière aléatoire à ses éléments. La classe `concurrent_vector` permet les opérations d’ajout et d’accès à l’élément sécurisées pour l’accès concurrentiel. Les opérations d’ajout n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de parcours sont également sécurisés pour la concurrence. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

###  <a name="vector-differences"></a>Différences entre concurrent_vector et Vector

La classe `concurrent_vector` ressemble étroitement à la classe `vector`. La complexité des opérations d’ajout, d’accès aux éléments et d’accès aux itérateurs sur un objet `concurrent_vector` est identique à celle d’un objet `vector`. Les points suivants illustrent où `concurrent_vector` diffère de `vector`:

- Les opérations d’ajout, d’accès aux éléments, d’accès aux itérateurs et de parcours des itérateurs sur un objet `concurrent_vector` sont sécurisées.

- Vous pouvez uniquement ajouter des éléments à la fin d’un objet `concurrent_vector`. La classe `concurrent_vector` ne fournit pas la méthode `insert`.

- Un objet `concurrent_vector` n’utilise pas la [sémantique de déplacement](../../cpp/rvalue-reference-declarator-amp-amp.md) lorsque vous l’ajoutez.

- La classe `concurrent_vector` ne fournit pas les méthodes `erase` ou `pop_back`. Comme avec `vector`, utilisez la méthode [Clear](reference/concurrent-vector-class.md#clear) pour supprimer tous les éléments d’un objet `concurrent_vector`.

- La classe `concurrent_vector` ne stocke pas ses éléments de façon contiguë en mémoire. Par conséquent, vous ne pouvez pas utiliser la classe `concurrent_vector` de toutes les façons d’utiliser un tableau. Par exemple, pour une variable nommée `v` de type `concurrent_vector`, l’expression `&v[0]+2` produit un comportement indéfini.

- La classe `concurrent_vector` définit les méthodes de [grow_by](reference/concurrent-vector-class.md#grow_by) et de [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Ces méthodes ressemblent à la méthode [Resize](reference/concurrent-vector-class.md#resize) , sauf qu’elles sont sécurisées.

- Un objet `concurrent_vector` ne déplace pas ses éléments lorsque vous l’ajoutez ou le redimensionnez. Cela permet aux pointeurs et itérateurs existants de rester valides pendant les opérations simultanées.

- Le runtime ne définit pas une version spécialisée de `concurrent_vector` pour le type `bool`.

###  <a name="vector-safety"></a>Opérations sécurisées pour l’accès concurrentiel

Toutes les méthodes qui ajoutent ou augmentent la taille d’un objet `concurrent_vector`, ou qui accèdent à un élément dans un objet `concurrent_vector`, sont sécurisées. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. L’exception à cette règle est la méthode `resize`.

Le tableau suivant présente les méthodes de `concurrent_vector` courantes et les opérateurs qui sont sécurisés pour l’accès concurrentiel.

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[begin](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[back](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[capacity](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

Les opérations que le Runtime fournit pour la compatibilité C++ avec la bibliothèque standard, par exemple, `reserve`, ne sont pas sécurisées pour l’accès concurrentiel. Le tableau suivant répertorie les méthodes et les opérateurs courants qui ne sont pas sécurisés pour la simultanéité.

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[reserve](reference/concurrent-vector-class.md#reserve)|
|[clear](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Les opérations qui modifient la valeur des éléments existants ne sont pas sécurisées pour l’accès concurrentiel. Utilisez un objet de synchronisation, tel qu’un objet [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) pour synchroniser les opérations de lecture et d’écriture simultanées avec le même élément de données. Pour plus d’informations sur les objets de synchronisation, consultez [structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md).

Lorsque vous convertissez du code existant qui utilise `vector` pour utiliser des `concurrent_vector`, les opérations simultanées peuvent entraîner la modification du comportement de votre application. Par exemple, considérez le programme suivant qui effectue simultanément deux tâches sur un objet `concurrent_vector`. La première tâche ajoute des éléments supplémentaires à un objet `concurrent_vector`. La deuxième tâche calcule la somme de tous les éléments dans le même objet.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Bien que la méthode `end` soit de sécurité simultanée, un appel simultané à la méthode [push_back](reference/concurrent-vector-class.md#push_back) entraîne la modification de la valeur retournée par `end`. Le nombre d’éléments que l’itérateur traverse est indéterminé. Par conséquent, ce programme peut produire un résultat différent chaque fois que vous l’exécutez. Lorsque le type d’élément n’est pas trivial, il est possible qu’une condition de concurrence existe entre les appels `push_back` et `end`. La méthode `end` peut retourner un élément qui est alloué, mais qui n’est pas complètement initialisé.

###  <a name="vector-exceptions"></a>Sécurité des exceptions

Si une opération de croissance ou d’assignation lève une exception, l’état de l’objet `concurrent_vector` devient non valide. Le comportement d’un objet `concurrent_vector` qui est dans un État non valide n’est pas défini, sauf indication contraire. Toutefois, le destructeur libère toujours la mémoire que l’objet alloue, même si l’objet est dans un État non valide.

Le type de données des éléments vectoriels, `T`, doit respecter les exigences suivantes. Dans le cas contraire, le comportement de la classe `concurrent_vector` n’est pas défini.

- Le destructeur ne doit pas lever d’exception.

- Si le constructeur de copie ou par défaut lève, le destructeur ne doit pas être déclaré à l’aide du mot clé `virtual` et il doit fonctionner correctement avec la mémoire initialisée à zéro.

[[Haut](#top)]

##  <a name="queue"></a>Classe concurrent_queue

La classe [Concurrency :: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , tout comme la classe [std :: queue](../../standard-library/queue-class.md) , vous permet d’accéder à ses éléments d’avant et de retour. La classe `concurrent_queue` permet d’effectuer des opérations de mise en file d’attente et de retrait de la file d’attente sécurisées. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. La classe `concurrent_queue` fournit également la prise en charge de l’itérateur qui n’est pas sécurisée pour l’accès concurrentiel.

###  <a name="queue-differences"></a>Différences entre les concurrent_queue et la file d’attente

La classe `concurrent_queue` ressemble étroitement à la classe `queue`. Les points suivants illustrent où `concurrent_queue` diffère de `queue`:

- Les opérations de mise en file d’attente et de retrait de la file d’attente sur un objet `concurrent_queue` sont sécurisées.

- La classe `concurrent_queue` fournit une prise en charge d’itérateur qui n’est pas sécurisée pour l’accès concurrentiel.

- La classe `concurrent_queue` ne fournit pas les méthodes `front` ou `pop`. La classe `concurrent_queue` remplace ces méthodes en définissant la méthode [try_pop](reference/concurrent-queue-class.md#try_pop) .

- La classe `concurrent_queue` ne fournit pas la méthode `back`. Par conséquent, vous ne pouvez pas référencer la fin de la file d’attente.

- La classe `concurrent_queue` fournit la méthode [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) à la place de la méthode `size`. La méthode `unsafe_size` n’est pas sécurisée pour la concurrence.

###  <a name="queue-safety"></a>Opérations sécurisées pour l’accès concurrentiel

Toutes les méthodes qui sont empilées ou déplacées en file d’attente d’un objet `concurrent_queue` sont sécurisées. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

Le tableau suivant présente les méthodes de `concurrent_queue` courantes et les opérateurs qui sont sécurisés pour l’accès concurrentiel.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Bien que la méthode `empty` soit sécurisée pour l’accès concurrentiel, une opération simultanée peut provoquer l’augmentation ou la réduction de la file d’attente avant le retour de la méthode `empty`.

Le tableau suivant répertorie les méthodes et les opérateurs courants qui ne sont pas sécurisés pour la simultanéité.

|||
|-|-|
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

###  <a name="queue-iterators"></a>Prise en charge des itérateurs

Le `concurrent_queue` fournit des itérateurs qui ne sont pas sécurisés pour la simultanéité. Nous vous recommandons d’utiliser ces itérateurs uniquement pour le débogage.

Un itérateur de `concurrent_queue` parcourt les éléments uniquement dans la direction avant. Le tableau suivant indique les opérateurs pris en charge par chaque itérateur.

|opérateur|Description|
|--------------|-----------------|
|`operator++`|Avance jusqu’à l’élément suivant dans la file d’attente. Cet opérateur est surchargé pour fournir une sémantique pré-incrémentée et postérieure à l’incrémentation.|
|`operator*`|Récupère une référence à l’élément actuel.|
|`operator->`|Récupère un pointeur vers l’élément actuel.|

[[Haut](#top)]

##  <a name="unordered_map"></a>Classe concurrent_unordered_map

La classe [Concurrency :: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) est une classe de conteneur associatif qui, tout comme la classe [std :: unordered_map](../../standard-library/unordered-map-class.md) , contrôle une séquence de longueur variable d’éléments de type [std ::P air\<const Key, Ty >](../../standard-library/pair-structure.md). Imaginez une carte non triée comme un dictionnaire auquel vous pouvez ajouter une paire clé/valeur ou rechercher une valeur par clé. Cette classe est utile lorsque vous avez plusieurs threads ou tâches qui doivent accéder simultanément à un conteneur partagé, les insérer ou les mettre à jour.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_map`. Cet exemple insère des touches de caractère dans la plage ['a', 'i']. Étant donné que l’ordre des opérations n’est pas déterminé, la valeur finale de chaque clé est également indéterminée. Toutefois, il est possible d’effectuer des insertions en parallèle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Pour obtenir un exemple qui utilise `concurrent_unordered_map` pour effectuer une opération de mappage et de réduction en parallèle, consultez [Comment : effectuer des opérations de mappage et de réduction en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

###  <a name="map-differences"></a>Différences entre concurrent_unordered_map et unordered_map

La classe `concurrent_unordered_map` ressemble étroitement à la classe `unordered_map`. Les points suivants illustrent où `concurrent_unordered_map` diffère de `unordered_map`:

- Les méthodes `erase`, `bucket`, `bucket_count`et `bucket_size` sont nommées `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`et `unsafe_bucket_size`, respectivement. La Convention d’affectation de noms `unsafe_` indique que ces méthodes ne sont pas sécurisées pour l’accès concurrentiel. Pour plus d’informations sur la sécurité de l’accès concurrentiel, consultez [opérations sécurisées pour l’accès concurrentiel](#map-safety).

- Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants, ni ne modifient l’ordre des éléments qui existent déjà dans le mappage. Les opérations d’insertion et de parcours peuvent se produire simultanément.

- `concurrent_unordered_map` prend en charge uniquement l’itération vers l’avant.

- L’insertion n’invalide pas ou ne met pas à jour les itérateurs retournés par `equal_range`. L’insertion peut ajouter des éléments inégaux à la fin de la plage. L’itérateur de début pointe sur un élément égal.

Pour éviter tout blocage, aucune méthode de `concurrent_unordered_map` ne détient un verrou lorsqu’il appelle l’allocateur de mémoire, les fonctions de hachage ou tout autre code défini par l’utilisateur. En outre, vous devez vous assurer que la fonction de hachage évalue toujours les clés égales à la même valeur. Les meilleures fonctions de hachage distribuent uniformément les clés dans l’espace de code de hachage.

###  <a name="map-safety"></a>Opérations sécurisées pour l’accès concurrentiel

La classe `concurrent_unordered_map` permet d’effectuer des opérations d’insertion et d’accès aux éléments sécurisés. Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de parcours sont également sécurisés pour la concurrence. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. Le tableau suivant répertorie les méthodes `concurrent_unordered_map` couramment utilisées et les opérateurs qui sont sécurisés pour l’accès concurrentiel.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

Bien que la méthode `count` puisse être appelée en toute sécurité à partir de threads exécutés simultanément, différents threads peuvent recevoir des résultats différents si une nouvelle valeur est insérée simultanément dans le conteneur.

Le tableau suivant répertorie les méthodes et les opérateurs couramment utilisés qui ne sont pas sécurisés pour la simultanéité.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

En plus de ces méthodes, toute méthode qui commence par `unsafe_` n’est pas non plus concurrentielle.

[[Haut](#top)]

##  <a name="unordered_multimap"></a>Classe concurrent_unordered_multimap

La classe [Concurrency :: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) ressemble étroitement à la classe `concurrent_unordered_map`, sauf qu’elle permet de mapper plusieurs valeurs à la même clé. Elle diffère également de `concurrent_unordered_map` des manières suivantes :

- La méthode [concurrent_unordered_multimap :: Insert](reference/concurrent-unordered-multimap-class.md#insert) retourne un itérateur au lieu de `std::pair<iterator, bool>`.

- La classe `concurrent_unordered_multimap` ne fournit pas `operator[]` ni la méthode `at`.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_multimap`. Cet exemple insère des touches de caractère dans la plage ['a', 'i']. `concurrent_unordered_multimap` permet à une clé d’avoir plusieurs valeurs.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Haut](#top)]

##  <a name="unordered_set"></a>Classe concurrent_unordered_set

La classe [Concurrency :: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) ressemble étroitement à la classe `concurrent_unordered_map`, sauf qu’elle gère des valeurs au lieu de paires clé/valeur. La classe `concurrent_unordered_set` ne fournit pas `operator[]` ni la méthode `at`.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_set`. Cet exemple insère des valeurs de caractère dans la plage ['a', 'i']. Il est possible d’effectuer des insertions en parallèle en toute sécurité.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Haut](#top)]

##  <a name="unordered_multiset"></a>Classe concurrent_unordered_multiset

La classe [Concurrency :: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) ressemble étroitement à la classe `concurrent_unordered_set`, sauf qu’elle autorise les valeurs dupliquées. Elle diffère également de `concurrent_unordered_set` des manières suivantes :

- La méthode [concurrent_unordered_multiset :: Insert](reference/concurrent-unordered-multiset-class.md#insert) retourne un itérateur au lieu de `std::pair<iterator, bool>`.

- La classe `concurrent_unordered_multiset` ne fournit pas `operator[]` ni la méthode `at`.

L’exemple suivant illustre la structure de base pour l’utilisation de `concurrent_unordered_multiset`. Cet exemple insère des valeurs de caractère dans la plage ['a', 'i']. `concurrent_unordered_multiset` permet à une valeur de se produire plusieurs fois.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Haut](#top)]

##  <a name="combinable"></a>combinable, classe

La classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) fournit un stockage local des threads réutilisable qui vous permet d’effectuer des calculs affinés, puis de fusionner ces calculs dans un résultat final. Vous pouvez considérer un objet `combinable` comme une variable de réduction.

La classe `combinable` est utile lorsque vous disposez d’une ressource qui est partagée entre plusieurs threads ou tâches. La classe `combinable` vous permet d’éliminer l’état partagé en fournissant un accès à des ressources partagées sans verrou. Par conséquent, cette classe fournit une alternative à l’utilisation d’un mécanisme de synchronisation, par exemple un mutex, pour synchroniser l’accès aux données partagées à partir de plusieurs threads.

###  <a name="combinable-features"></a>Méthodes et fonctionnalités

Le tableau suivant présente quelques-unes des méthodes importantes de la classe `combinable`. Pour plus d’informations sur toutes les méthodes de la classe `combinable`, consultez [classe combinable](../../parallel/concrt/reference/combinable-class.md).

|Méthode|Description|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Récupère une référence à la variable locale associée au contexte de thread actuel.|
|[clear](reference/combinable-class.md#clear)|Supprime toutes les variables de thread local de l’objet `combinable`.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Utilise la fonction combine fournie pour générer une valeur finale à partir de l’ensemble de tous les calculs locaux de thread.|

La classe `combinable` est une classe de modèle paramétrable sur le résultat final fusionné. Si vous appelez le constructeur par défaut, le `T` type de paramètre de modèle doit avoir un constructeur par défaut et un constructeur de copie. Si le type de paramètre de modèle `T` n’a pas de constructeur par défaut, appelez la version surchargée du constructeur qui prend une fonction d’initialisation comme paramètre.

Vous pouvez stocker des données supplémentaires dans un objet `combinable` une fois que vous avez appelé les méthodes [combine](reference/combinable-class.md#combine) ou [combine_each](reference/combinable-class.md#combine_each) . Vous pouvez également appeler les méthodes `combine` et `combine_each` plusieurs fois. Si aucune valeur locale dans un objet `combinable` n’est modifiée, les méthodes `combine` et `combine_each` produisent le même résultat chaque fois qu’elles sont appelées.

###  <a name="combinable-examples"></a> Exemples

Pour obtenir des exemples d’utilisation de la classe `combinable`, consultez les rubriques suivantes :

- [Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Guide pratique pour utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Haut](#top)]

## <a name="related-topics"></a>Rubriques connexes

[Guide pratique pour utiliser des conteneurs parallèles pour une efficacité accrue](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Montre comment utiliser des conteneurs parallèles pour stocker et accéder efficacement aux données en parallèle.

[Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Montre comment utiliser la classe `combinable` pour éliminer l’état partagé et ainsi améliorer les performances.

[Guide pratique pour utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Montre comment utiliser une fonction `combine` pour fusionner des jeux de données de thread local.

[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Décrit la bibliothèque PPL, qui fournit un modèle de programmation impératif qui favorise l’évolutivité et la facilité d’utilisation du développement d’applications simultanées.

## <a name="reference"></a>Reference

[concurrent_vector, classe](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue, classe](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map, classe](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap, classe](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set, classe](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset, classe](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable, classe](../../parallel/concrt/reference/combinable-class.md)
