---
title: Conteneurs et objets parallèles
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363045"
---
# <a name="parallel-containers-and-objects"></a>Conteneurs et objets parallèles

La Bibliothèque des motifs parallèles (PPL) comprend plusieurs conteneurs et objets qui offrent un accès sûr aux fils de leurs éléments.

Un *conteneur simultané* offre un accès en toute sécurité aux opérations les plus importantes. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier. La fonctionnalité de ces conteneurs ressemble à celles fournies par la Bibliothèque standard de C. Par exemple, la [concordance: :concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe ressemble à la [std::classe vectorielle,](../../standard-library/vector-class.md) sauf que la `concurrent_vector` classe vous permet d’ajouter des éléments en parallèle. Utilisez des contenants simultanés lorsque vous avez un code parallèle qui nécessite à la fois lire et écrire l’accès au même conteneur.

Un *objet concurrent* est partagé simultanément entre les composants. Un processus qui calcule l’état d’un objet concurrent en parallèle produit le même résultat qu’un autre processus qui calcule le même état en série. La [concordance: :la classe combinable](../../parallel/concrt/reference/combinable-class.md) est un exemple d’un type d’objet simultané. La `combinable` classe vous permet d’effectuer des calculs en parallèle, puis de combiner ces calculs dans un résultat final. Utilisez des objets simultanés lorsque vous utilisez autrement un mécanisme de synchronisation, par exemple, un mutex, pour synchroniser l’accès à une variable ou à une ressource partagée.

## <a name="sections"></a><a name="top"></a>Sections

Ce sujet décrit en détail les conteneurs et objets parallèles suivants.

Conteneurs simultanés :

- [Classe concurrent_vector](#vector)

  - [Différences entre concurrent_vector et vecteur](#vector-differences)

  - [Opérations de sécurité de la concurrence](#vector-safety)

  - [Sécurité d’exception](#vector-exceptions)

- [concurrent_queue, classe](#queue)

  - [Différences entre concurrent_queue et file d’attente](#queue-differences)

  - [Opérations de sécurité de la concurrence](#queue-safety)

  - [Soutien aux itérateurs](#queue-iterators)

- [Classe concurrent_unordered_map](#unordered_map)

  - [Différences entre concurrent_unordered_map et unordered_map](#map-differences)

  - [Opérations de sécurité de la concurrence](#map-safety)

- [concurrent_unordered_multimap, classe](#unordered_multimap)

- [concurrent_unordered_set, classe](#unordered_set)

- [Classe concurrent_unordered_multiset](#unordered_multiset)

Objets concomitants :

- [Classe combinable](#combinable)

  - [Méthodes et caractéristiques](#combinable-features)

  - [Exemples](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>Classe concurrent_vector

La [concordance: :concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe est une classe de conteneurs séquence qui, tout comme le [std::classe vector,](../../standard-library/vector-class.md) vous permet d’accéder au hasard à ses éléments. La `concurrent_vector` classe permet des opérations d’appendice et d’accès aux éléments en toute sécurité. Les opérations d’append entend n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de travers sont également en sécurité. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Différences entre concurrent_vector et vecteur

La `concurrent_vector` classe ressemble `vector` beaucoup à la classe. La complexité de l’appendice, de l’accès aux éléments et des opérations d’accès à l’itérateur sur un `concurrent_vector` objet est la même que pour un `vector` objet. Les points suivants `concurrent_vector` illustrent `vector`où diffère de :

- Les opérations d’appendice, d’accès aux éléments, `concurrent_vector` d’accès à l’itérateur et des opérations de traversée des itérateurs sur un objet sont en toute sécurité.

- Vous ne pouvez ajouter des `concurrent_vector` éléments qu’à la fin d’un objet. La `concurrent_vector` classe ne `insert` fournit pas la méthode.

- Un `concurrent_vector` objet n’utilise pas [la sémantique de mouvement](../../cpp/rvalue-reference-declarator-amp-amp.md) lorsque vous y arrivez.

- La `concurrent_vector` classe ne `erase` fournit `pop_back` pas les méthodes ou les méthodes. Comme `vector`avec , utilisez la méthode [claire](reference/concurrent-vector-class.md#clear) pour supprimer tous les éléments d’un `concurrent_vector` objet.

- La `concurrent_vector` classe ne stocke pas ses éléments de mémoire. Par conséquent, vous `concurrent_vector` ne pouvez pas utiliser la classe de toutes les façons que vous pouvez utiliser un tableau. Par exemple, pour `v` une `concurrent_vector`variable nommée `&v[0]+2` de type, l’expression produit un comportement indéfini.

- La `concurrent_vector` classe définit les méthodes [grow_by](reference/concurrent-vector-class.md#grow_by) et [grow_to_at_least.](reference/concurrent-vector-class.md#grow_to_at_least) Ces méthodes ressemblent à la méthode [de redimensionnement,](reference/concurrent-vector-class.md#resize) sauf qu’elles sont en sécurité.

- Un `concurrent_vector` objet ne déplace pas ses éléments lorsque vous l’appendiciez ou ne le resize. Cela permet aux pointeurs et itérateurs existants de rester valides pendant les opérations simultanées.

- L’exécution ne définit pas `concurrent_vector` une `bool`version spécialisée de type .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Opérations de sécurité de la concurrence

Toutes les méthodes qui s’appendicent ou augmentent la taille d’un `concurrent_vector` objet, ou accèdent à un élément d’un `concurrent_vector` objet, sont en sécurité. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier. L’exception à cette `resize` règle est la méthode.

Le tableau suivant `concurrent_vector` montre les méthodes et les opérateurs communs qui sont en sécurité.

||||
|-|-|-|
|[À](reference/concurrent-vector-class.md#at)|[Fin](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[Commencer](reference/concurrent-vector-class.md#begin)|[Avant](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Précédent](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[Capacité](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[Vide](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[Taille](reference/concurrent-vector-class.md#size)|

Les opérations que le temps d’exécution prévoit la compatibilité `reserve`avec la Bibliothèque standard de C, par exemple, ne sont pas compatibles avec la sécurité. Le tableau suivant montre les méthodes et les opérateurs communs qui ne sont pas en sécurité.

|||
|-|-|
|[Attribuer](reference/concurrent-vector-class.md#assign)|[Réserve](reference/concurrent-vector-class.md#reserve)|
|[Clair](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[opérateur](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Les opérations qui modifient la valeur des éléments existants ne sont pas en sécurité. Utilisez un objet de synchronisation tel qu’un objet [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) pour synchroniser les opérations de lecture et d’écriture simultanées sur le même élément de données. Pour plus d’informations sur les objets de synchronisation, voir [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md).

Lorsque vous convertissez `vector` le `concurrent_vector`code existant qui utilise, les opérations simultanées peuvent provoquer la modification du comportement de votre application. Par exemple, considérez le programme suivant qui `concurrent_vector` effectue simultanément deux tâches sur un objet. La première tâche appende `concurrent_vector` des éléments supplémentaires à un objet. La deuxième tâche calcule la somme de tous les éléments dans le même objet.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Bien `end` que la méthode soit en sécurité, un appel simultané à la méthode `end` [push_back](reference/concurrent-vector-class.md#push_back) fait changer la valeur qui est retournée. Le nombre d’éléments que traverse l’itérateur est indéterminé. Par conséquent, ce programme peut produire un résultat différent chaque fois que vous l’exécutez. Lorsque le type d’élément n’est pas négligeable, il `push_back` `end` est possible qu’une condition de course existe entre et les appels. La `end` méthode peut retourner un élément qui est alloué, mais pas entièrement initialisé.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Sécurité d’exception

Si une opération de croissance ou d’affectation `concurrent_vector` fait une exception, l’état de l’objet devient invalide. Le comportement `concurrent_vector` d’un objet qui est dans un état invalide n’est pas défini à moins d’être indiqué autrement. Cependant, le destructeur libère toujours la mémoire que l’objet attribue, même si l’objet est dans un état invalide.

Le type de données `T`des éléments vectoriels, doit répondre aux exigences suivantes. Sinon, le comportement `concurrent_vector` de la classe n’est pas défini.

- Le destructeur ne doit pas jeter.

- Si le constructeur par défaut ou le constructeur de copie jette, le destructeur ne doit pas être déclaré en utilisant le `virtual` mot clé et il doit fonctionner correctement avec la mémoire zéro-initialisée.

[[Top](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>Classe concurrent_queue

La [concordance::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) classe, tout comme le [std::classe de file d’attente,](../../standard-library/queue-class.md) vous permet d’accéder à ses éléments avant et arrière. La `concurrent_queue` classe permet des opérations d’enqueue et dequeue en plus sûres. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier. La `concurrent_queue` classe fournit également un soutien itérateur qui n’est pas en sécurité.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Différences entre concurrent_queue et file d’attente

La `concurrent_queue` classe ressemble `queue` beaucoup à la classe. Les points suivants `concurrent_queue` illustrent `queue`où diffère de :

- Les opérations d’enqueue `concurrent_queue` et dequeue sur un objet sont en sécurité.

- La `concurrent_queue` classe fournit un soutien itérateur qui n’est pas en sécurité.

- La `concurrent_queue` classe ne `front` fournit `pop` pas les méthodes ou les méthodes. La `concurrent_queue` classe remplace ces méthodes en définissant la [méthode try_pop.](reference/concurrent-queue-class.md#try_pop)

- La `concurrent_queue` classe ne `back` fournit pas la méthode. Par conséquent, vous ne pouvez pas faire référence à la fin de la file d’attente.

- La `concurrent_queue` classe fournit la [méthode unsafe_size](reference/concurrent-queue-class.md#unsafe_size) `size` au lieu de la méthode. La `unsafe_size` méthode n’est pas de concurrence-sûr.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Opérations de sécurité de la concurrence

Toutes les méthodes qui engueissent ouquent à partir d’un `concurrent_queue` objet sont concurrency-safe. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier.

Le tableau suivant `concurrent_queue` montre les méthodes et les opérateurs communs qui sont en sécurité.

|||
|-|-|
|[Vide](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Bien `empty` que la méthode soit en sécurité, une opération simultanée peut `empty` faire croître ou rétrécir la file d’attente avant le retour de la méthode.

Le tableau suivant montre les méthodes et les opérateurs communs qui ne sont pas en sécurité.

|||
|-|-|
|[Clair](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Soutien aux itérateurs

Les `concurrent_queue` itérateurs fournissent des itérateurs qui ne sont pas en sécurité de concurrence. Nous vous recommandons d’utiliser ces itérateurs pour débogage seulement.

Un `concurrent_queue` itérateur traverse des éléments dans la direction avant seulement. Le tableau suivant montre aux opérateurs que chaque itérateur prend en charge.

|Opérateur|Description|
|--------------|-----------------|
|`operator++`|Avance à l’élément suivant dans la file d’attente. Cet opérateur est surchargé pour fournir à la fois la sémantique pré-incrément et après l’incrément.|
|`operator*`|Récupère une référence à l’élément actuel.|
|`operator->`|Récupère un pointeur sur l’élément actuel.|

[[Top](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>Classe concurrent_unordered_map

La [concordance: :concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) classe est une classe de conteneurs associatifs qui, tout comme la [std::unordered_map](../../standard-library/unordered-map-class.md) classe, contrôle une séquence de longueur variable d’éléments de type [std::pair\<const Key, Ty>](../../standard-library/pair-structure.md). Pensez à une carte non ordonnée comme un dictionnaire que vous pouvez ajouter une touche et la paire de valeur à ou rechercher une valeur par clé. Cette classe est utile lorsque vous avez plusieurs threads ou tâches qui doivent accéder simultanément à un conteneur partagé, y insérer ou le mettre à jour.

L’exemple suivant montre la `concurrent_unordered_map`structure de base pour l’utilisation . Cet exemple insère les touches de caractère dans la gamme ['a', 'i']. Étant donné que l’ordre des opérations est indéterminé, la valeur finale de chaque clé est également indéterminée. Cependant, il est sûr d’effectuer les insertions en parallèle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Par exemple, `concurrent_unordered_map` qui utilise pour effectuer une carte et réduire l’exploitation en parallèle, voir [Comment effectuer la carte et réduire les opérations en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Différences entre concurrent_unordered_map et unordered_map

La `concurrent_unordered_map` classe ressemble `unordered_map` beaucoup à la classe. Les points suivants `concurrent_unordered_map` illustrent `unordered_map`où diffère de :

- Le `erase` `bucket`, `bucket_count`, `bucket_size` , `unsafe_erase`et `unsafe_bucket` `unsafe_bucket_count`les `unsafe_bucket_size`méthodes sont nommés , , , et , respectivement. La `unsafe_` convention de nommage indique que ces méthodes ne sont pas en sécurité. Pour plus d’informations sur la sécurité de la concurrence, voir [Opérations De concurrency-Safe](#map-safety).

- Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants, ni l’ordre des éléments qui existent déjà dans la carte. Les opérations d’insertion et de traversée peuvent se produire simultanément.

- `concurrent_unordered_map`supporte uniquement l’itération vers l’avant.

- L’insertion n’invalide pas ou ne `equal_range`met pas à jour les itérateurs qui sont retournés par . L’insertion peut appendice des éléments inégaux à la fin de la plage. L’itérateur de départ indique un élément égal.

Pour éviter l’impasse, `concurrent_unordered_map` aucune méthode de blocage n’est utilisée lorsqu’elle appelle l’alloueur de mémoire, les fonctions de hachage ou tout autre code défini par l’utilisateur. En outre, vous devez vous assurer que la fonction de hachage évalue toujours les clés égales à la même valeur. Les meilleures fonctions de hachage distribuent uniformément les clés à travers l’espace de code de hachage.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Opérations de sécurité de la concurrence

La `concurrent_unordered_map` classe permet des opérations d’insertion et d’accès aux éléments. Les opérations d’insertion n’invalident pas les pointeurs ou les itérateurs existants. L’accès aux itérateurs et les opérations de travers sont également en sécurité. Ici, les conseils de sécurité de concurrence-sûr sont toujours valables. Ce n’est pas une garantie d’initialisation d’éléments, ou d’un ordre de traversal particulier. Le tableau suivant montre `concurrent_unordered_map` les méthodes couramment utilisées et les opérateurs qui sont en sécurité de concurrence.

|||||
|-|-|-|-|
|[À](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Insérer](reference/concurrent-unordered-map-class.md#insert)|`size`|

Bien `count` que la méthode puisse être appelée en toute sécurité à partir de threads en cours d’exécution simultanée, différents threads peuvent recevoir des résultats différents si une nouvelle valeur est simultanément insérée dans le conteneur.

Le tableau suivant montre les méthodes couramment utilisées et les opérateurs qui ne sont pas en sécurité.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[opérateur](reference/concurrent-unordered-map-class.md#operator_eq)

En plus de ces méthodes, `unsafe_` toute méthode qui commence par n’est pas non plus de concurrence-sûr.

[[Top](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>Classe concurrent_unordered_multimap

La [concordance: :concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) classe ressemble beaucoup `concurrent_unordered_map` à la classe, sauf qu’il permet à plusieurs valeurs de cartographier à la même clé. Il diffère également `concurrent_unordered_map` de la façon suivante :

- Le [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) méthode retourne un itérateur `std::pair<iterator, bool>`au lieu de .

- La `concurrent_unordered_multimap` classe ne `operator[]` fournit `at` ni la méthode.

L’exemple suivant montre la `concurrent_unordered_multimap`structure de base pour l’utilisation . Cet exemple insère les touches de caractère dans la gamme ['a', 'i']. `concurrent_unordered_multimap`permet à une clé d’avoir plusieurs valeurs.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Top](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>Classe concurrent_unordered_set

La [concordance : : concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) classe ressemble `concurrent_unordered_map` beaucoup à la classe, sauf qu’elle gère des valeurs au lieu des paires de clés et de valeurs. La `concurrent_unordered_set` classe ne `operator[]` fournit `at` ni la méthode.

L’exemple suivant montre la `concurrent_unordered_set`structure de base pour l’utilisation . Cet exemple insère les valeurs de caractère dans la gamme ['a', 'i']. Il est sécuritaire d’effectuer les insertions en parallèle.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Top](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>Classe concurrent_unordered_multiset

La [concordance: :concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) classe ressemble beaucoup à `concurrent_unordered_set` la classe, sauf qu’il permet des valeurs en double. Il diffère également `concurrent_unordered_set` de la façon suivante :

- Le [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) méthode retourne un itérateur au lieu de `std::pair<iterator, bool>`.

- La `concurrent_unordered_multiset` classe ne `operator[]` fournit `at` ni la méthode.

L’exemple suivant montre la `concurrent_unordered_multiset`structure de base pour l’utilisation . Cet exemple insère les valeurs de caractère dans la gamme ['a', 'i']. `concurrent_unordered_multiset`permet à une valeur de se produire plusieurs fois.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Top](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>Classe combinable

La [concordance::la classe combinable](../../parallel/concrt/reference/combinable-class.md) fournit réutilisable, thread-local stockage qui vous permet d’effectuer des calculs à grain fin, puis de fusionner ces calculs dans un résultat final. Vous pouvez considérer un objet `combinable` comme une variable de réduction.

La `combinable` classe est utile lorsque vous avez une ressource qui est partagée entre plusieurs threads ou tâches. La `combinable` classe vous aide à éliminer l’état partagé en donnant accès à des ressources partagées d’une manière sans verrou. Par conséquent, cette classe offre une alternative à l’utilisation d’un mécanisme de synchronisation, par exemple, un mutex, pour synchroniser l’accès aux données partagées à partir de plusieurs threads.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Méthodes et caractéristiques

Le tableau suivant montre quelques-unes des méthodes importantes de la `combinable` classe. Pour plus d’informations sur toutes les méthodes de `combinable` classe, voir classe [combinable](../../parallel/concrt/reference/combinable-class.md).

|Méthode|Description|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Récupère une référence à la variable locale associée au contexte de thread actuel.|
|[Clair](reference/combinable-class.md#clear)|Supprime toutes les variables thread-local de l’objet. `combinable`|
|[Combiner](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Utilise la fonction de combine fournie pour générer une valeur finale à partir de l’ensemble de tous les calculs thread-local.|

La `combinable` classe est une classe de modèle qui est paramétrée sur le résultat final fusionné. Si vous appelez le constructeur `T` par défaut, le type de paramètre de modèle doit avoir un constructeur par défaut et un constructeur de copie. Si `T` le type de paramètre de modèle n’a pas de constructeur par défaut, appelez la version surchargée du constructeur qui prend une fonction d’initialisation comme paramètre.

Vous pouvez stocker des `combinable` données supplémentaires dans un objet après avoir appelé les méthodes [de moissonneuse-batteuse](reference/combinable-class.md#combine) ou [combine_each.](reference/combinable-class.md#combine_each) Vous pouvez également `combine` `combine_each` appeler les méthodes et les méthodes plusieurs fois. Si aucune valeur `combinable` locale dans `combine` un `combine_each` objet ne change, le et les méthodes produisent le même résultat chaque fois qu’ils sont appelés.

### <a name="examples"></a><a name="combinable-examples"></a>Exemples

Pour des exemples `combinable` sur la façon d’utiliser la classe, voir les sujets suivants:

- [Comment : utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Comment : utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Top](#top)]

## <a name="related-topics"></a>Rubriques connexes

[Comment : utiliser des conteneurs parallèles pour une efficacité accrue](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Montre comment utiliser des conteneurs parallèles pour stocker et accéder efficacement aux données en parallèle.

[Comment : utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Montre comment utiliser `combinable` la classe pour éliminer l’état partagé, et ainsi améliorer les performances.

[Comment : utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Montre comment utiliser `combine` une fonction pour fusionner des ensembles de données thread-local.

[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Décrit le PPL, qui fournit un modèle de programmation impératif qui favorise l’évolutivité et la facilité d’utilisation pour le développement d’applications simultanées.

## <a name="reference"></a>Informations de référence

[Classe concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue, classe](../../parallel/concrt/reference/concurrent-queue-class.md)

[Classe concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap, classe](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set, classe](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[Classe concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[Classe combinable](../../parallel/concrt/reference/combinable-class.md)
