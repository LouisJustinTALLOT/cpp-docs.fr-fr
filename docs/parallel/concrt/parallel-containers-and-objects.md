---
title: Objets et conteneurs parallèles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8256a6d49166b5a002a400892f0808706c66eba9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212460"
---
# <a name="parallel-containers-and-objects"></a>Conteneurs et objets parallèles
La bibliothèque de modèles parallèles (PPL) inclut plusieurs conteneurs et objets qui fournissent l’accès thread-safe à leurs éléments.  
  
 Un *conteneur simultané* fournit l’accès concurrentiel pour les opérations les plus importantes. Les fonctionnalités de ces conteneurs est similaire à celles qui sont fournies par la bibliothèque Standard C++. Par exemple, le [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe est similaire à la [std::vector](../../standard-library/vector-class.md) classe, à ceci près que le `concurrent_vector` classe vous permet d’ajouter des éléments en parallèle. Utilisez des conteneurs simultanés lorsque vous avez du code parallèle qui requiert les accès en lecture et écriture dans le même conteneur.  
  
 Un *objet simultané* partagé simultanément entre composants. Un processus qui calcule l’état d’un objet simultané en parallèle produit le même résultat qu’un autre processus qui calcule le même état de façon séquentielle. Le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe est un exemple d’un type d’objet simultané. Le `combinable` classe vous permet d’effectuer des calculs en parallèle, puis combine ces calculs dans un résultat final. Utilisez des objets simultanés lorsque vous utiliseriez normalement un mécanisme de synchronisation, par exemple, un mutex, pour synchroniser l’accès à une variable partagée ou une ressource.  
  
##  <a name="top"></a> Sections  
 Cette rubrique décrit les objets en détail et des conteneurs parallèles suivants.  
  
 Conteneurs simultanés :  
  
-   [concurrent_vector, classe](#ctor)  
  
    -   [Différences entre concurrent_vector et Vector](#ctor)  
  
    -   [Opérations d’accès concurrentiel sécurisé](#ctor)  
  
    -   [Sécurité des exceptions](#ctor)  
  
-   [concurrent_queue, classe](#queue)  
  
    -   [File d’attente et les différences entre concurrent_queue](#queue-differences)  
  
    -   [Opérations d’accès concurrentiel sécurisé](#queue-safety)  
  
    -   [Prise en charge de l’itérateur](#queue-iterators)  
  
-   [concurrent_unordered_map, classe](#unordered_map)  
  
    -   [Unordered_map et les différences entre concurrent_unordered_map](#map-differences)  
  
    -   [Opérations d’accès concurrentiel sécurisé](#map-safety)  
  
-   [concurrent_unordered_multimap, classe](#unordered_multimap)  
  
-   [concurrent_unordered_set, classe](#unordered_set)  
  
-   [concurrent_unordered_multiset, classe](#unordered_multiset)  
  
 Les objets simultanés :  
  
-   [combinable, classe](#combinable)  
  
    -   [Méthodes et fonctionnalités](#combinable-features)  
  
    -   [Exemples](#combinable-examples)  
  
##  <a name="vector"></a> concurrent_vector, classe  
 Le [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe est une classe de conteneur de séquence qui, tout comme le [std::vector](../../standard-library/vector-class.md) de classe, vous permet d’accéder aléatoirement à ses éléments. Le `concurrent_vector` permet de classe concurrentiel append et élément accéder aux opérations. Ajouter des opérations n’invalident pas les pointeurs ou itérateurs existants. Itérateur d’accès et parcours opérations est également concurrentiel.  
  
###  <a name="vector-differences"></a> Différences entre concurrent_vector et Vector  
 Le `concurrent_vector` classe ressemble étroitement à la `vector` classe. La complexité de l’ajout, accès aux éléments et opérations d’accès itérateur sur une `concurrent_vector` objet sont les mêmes que pour un `vector` objet. Les points suivants illustrent où `concurrent_vector` diffère `vector`:  
  
-   Ajout, accès à un élément, itérateurs et opérations de traversée d’itérateur, sur un `concurrent_vector` objet sont concurrentiel.  
  
-   Vous pouvez ajouter des éléments uniquement à la fin d’un `concurrent_vector` objet. Le `concurrent_vector` classe ne fournit pas la `insert` (méthode).  
  
-   Un `concurrent_vector` objet n’utilise pas [la sémantique de déplacement](../../cpp/rvalue-reference-declarator-amp-amp.md) lorsque vous ajoutez à ce dernier.  
  

-   Le `concurrent_vector` classe ne fournit pas la `erase` ou `pop_back` méthodes. Comme avec `vector`, utilisez le [effacer](reference/concurrent-vector-class.md#clear) méthode pour supprimer tous les éléments à partir d’un `concurrent_vector` objet.  
  
-   Le `concurrent_vector` classe ne stocke pas les ses éléments de façon contiguë en mémoire. Par conséquent, vous ne pouvez pas utiliser le `concurrent_vector` classe dans toutes les méthodes que vous pouvez utiliser un tableau. Par exemple, pour une variable nommée `v` de type `concurrent_vector`, l’expression `&v[0]+2` produit un comportement non défini.  
  
-   Le `concurrent_vector` classe définit la [grow_by](reference/concurrent-vector-class.md#grow_by) et [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) méthodes. Ces méthodes ressemblent à la [redimensionner](reference/concurrent-vector-class.md#resize) (méthode), à ceci près qu’elles soient compatibles avec la concurrence.  
  
-   Un `concurrent_vector` objet ne déplace pas ses éléments lorsque vous redimensionnez ou s’y ajouter. Ainsi, les pointeurs existants et les itérateurs de rester valide pendant les opérations simultanées.  
  
-   Le runtime ne définit pas une version spécialisée de `concurrent_vector` pour le type `bool`.  
  
###  <a name="vector-safety"></a> Opérations d’accès concurrentiel sécurisé  
 Toutes les méthodes qui ajoutent à ou augmentent la taille d’un `concurrent_vector` de l’objet, ou accéder à un élément dans un `concurrent_vector` d’objet, sont compatibles avec la concurrence. L’exception à cette règle est la `resize` (méthode).  
  
 Le tableau suivant présente le commun `concurrent_vector` méthodes et opérateurs sont concurrentiel.  
  
||||  
|-|-|-|  

|[à](reference/concurrent-vector-class.md#at)|[fin](reference/concurrent-vector-class.md#end)|[opérateur&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|  
|[commencer](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|  
|[retour](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|  
|[capacité](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|  
|[vide](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[taille](reference/concurrent-vector-class.md#size)|  

  
 Opérations fournies par le runtime pour la compatibilité avec la bibliothèque C++ Standard, par exemple, `reserve`, ne sont pas compatibles avec la concurrence. Le tableau suivant montre les méthodes courantes et les opérateurs qui ne sont pas compatibles avec la concurrence.  
  
|||  
|-|-|  

|[affecter](reference/concurrent-vector-class.md#assign)|[réserver](reference/concurrent-vector-class.md#reserve)|  
|[Désactivez](reference/concurrent-vector-class.md#clear)|[redimensionner](reference/concurrent-vector-class.md#resize)|  
|[opérateur =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|  
  
 Les opérations qui modifient la valeur des éléments existants ne sont pas compatibles avec la concurrence. Utiliser un objet de synchronisation comme un [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objet à synchroniser simultanées en lecture et les opérations d’écriture pour le même élément de données. Pour plus d’informations sur les objets de synchronisation, consultez [les Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md).  
  
 Lorsque vous convertissez un code existant qui utilise `vector` à utiliser `concurrent_vector`, opérations simultanées peuvent provoquer un comportement de votre application à modifier. Par exemple, considérez le programme suivant qui exécute simultanément les deux tâches sur un `concurrent_vector` objet. La première tâche ajoute des éléments supplémentaires à un `concurrent_vector` objet. La deuxième tâche calcule la somme de tous les éléments dans le même objet.  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]  
  

 Bien que le `end` (méthode) est concurrentiel, un appel simultané à la [push_back](reference/concurrent-vector-class.md#push_back) méthode provoque la valeur retournée par `end` à modifier. Le nombre d’éléments parcourus par l’itérateur est indéterminé. Par conséquent, ce programme peut produire un résultat différent à chaque fois que vous l’exécutez.  
  
###  <a name="vector-exceptions"></a> Sécurité des exceptions  
 Si une opération d’assignation ou de croissance lève une exception, l’état de la `concurrent_vector` objet devient non valide. Le comportement d’un `concurrent_vector` objet qui se trouve dans un état non valide n’est pas défini, sauf spécification contraire. Toutefois, le destructeur libère toujours la mémoire allouée par l’objet, même si l’objet est dans un état non valide.  
  
 Le type de données des éléments de vecteur, `T`, doit remplir les conditions suivantes. Sinon, le comportement de la `concurrent_vector` classe n’est pas définie.  
  
-   Le destructeur ne doit pas lever.  
  
-   Si le constructeur de copie ou par défaut lève, le destructeur ne doit pas être déclaré à l’aide de la `virtual` mot clé et il doivent fonctionner correctement avec mémoire initialisée à zéro.  
  
 [[Haut](#top)]  
  
##  <a name="queue"></a> concurrent_queue, classe  
 Le [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) de classe, comme le [std::queue](../../standard-library/queue-class.md) de classe, vous permet d’accéder à son début et de sauvegarder des éléments. Le `concurrent_queue` classe file d’attente active concurrentiel et de la file d’attente des opérations. Le `concurrent_queue` classe fournit également des itérateurs prise en charge n’est pas d’accès concurrentiel sécurisé.  
  
###  <a name="queue-differences"></a> File d’attente et les différences entre concurrent_queue  
 Le `concurrent_queue` classe ressemble étroitement à la `queue` classe. Les points suivants illustrent où `concurrent_queue` diffère `queue`:  
  
-   File d’attente et la file d’attente des opérations sur un `concurrent_queue` objet sont concurrentiel.  
  
-   Le `concurrent_queue` classe prend en charge d’itérateur qui n’est pas d’accès concurrentiel sécurisé.  
  

-   Le `concurrent_queue` classe ne fournit pas la `front` ou `pop` méthodes. Le `concurrent_queue` classe remplace ces méthodes en définissant le [try_pop](reference/concurrent-queue-class.md#try_pop) (méthode).  
  
-   Le `concurrent_queue` classe ne fournit pas la `back` (méthode). Par conséquent, vous ne pouvez pas référencer la fin de la file d’attente.  
  
-   Le `concurrent_queue` classe fournit le [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) méthode au lieu du `size` (méthode). Le `unsafe_size` méthode n’est pas un accès concurrentiel sécurisé.  

  
###  <a name="queue-safety"></a> Opérations d’accès concurrentiel sécurisé  
 Toutes les méthodes de cette file d’attente à ou la file d’attente à partir d’un `concurrent_queue` objet sont concurrentiel.  
  
 Le tableau suivant présente le commun `concurrent_queue` méthodes et opérateurs sont concurrentiel.  
  
|||  
|-|-|  
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|  
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|  


  
 Bien que le `empty` (méthode) est concurrentiel, une opération simultanée peut provoquer la file d’attente agrandir ou réduire avant le `empty` méthode retourne.  
  
 Le tableau suivant montre les méthodes courantes et les opérateurs qui ne sont pas compatibles avec la concurrence.  
  
|||  
|-|-|  
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|  
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|  


  
###  <a name="queue-iterators"></a> Prise en charge de l’itérateur  
 Le `concurrent_queue` fournit des itérateurs qui ne sont pas compatibles avec la concurrence. Nous vous recommandons d’utiliser ces itérateurs uniquement pour le débogage.  
  
 Un `concurrent_queue` itérateur parcourt des éléments dans la direction vers l’avant uniquement. Le tableau suivant répertorie les opérateurs que chaque itérateur prend en charge.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[operator++](https://msdn.microsoft.com/4cfdd07e-927a-42f8-aaa0-d6881687f413)|Avance à l’élément suivant dans la file d’attente. Cet opérateur est surchargé pour fournir une sémantique incrément préliminaire et postérieures à l’incrémentation.|  
|[operator*](https://msdn.microsoft.com/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|Récupère une référence à l’élément actuel.|  
|[operator->](https://msdn.microsoft.com/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|Récupère un pointeur vers l’élément actuel.|  
  
 [[Haut](#top)]  
  
##  <a name="unordered_map"></a> concurrent_unordered_map, classe  
 Le [HYPERLINK « file:///C :\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default \\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622 » concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) classe est un classe de conteneur associatif qui, tout comme le [std::unordered_map](../../standard-library/unordered-map-class.md) class, contrôle une séquence de longueur variable constituée d’éléments de type [std::pair\<const Key, Ty >](../../standard-library/pair-structure.md). Considérez une carte non ordonnée en tant que dictionnaire que vous pouvez ajouter une paire clé / valeur à ou rechercher une valeur par clé. Cette classe est utile lorsque vous avez plusieurs threads ou tâches qui doivent accéder à un conteneur partagé, insérer ou mettre à jour simultanément.  
  
 L’exemple suivant montre la structure de base pour l’utilisation de `concurrent_unordered_map`. Cet exemple insère des touches de caractère dans la plage ['a', ' i']. Étant donné que l’ordre des opérations est indéterminé, la valeur finale pour chaque clé est également indéterminée. Toutefois, il est déconseillé d’effectuer des insertions en parallèle.  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]  
  
 Pour obtenir un exemple qui utilise `concurrent_unordered_map` pour effectuer un mappage et réduire les opérations en parallèle, consultez [Comment : effectuer un mappage et réduire les opérations en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
###  <a name="map-differences"></a> Unordered_map et les différences entre concurrent_unordered_map  
 Le `concurrent_unordered_map` classe ressemble étroitement à la `unordered_map` classe. Les points suivants illustrent où `concurrent_unordered_map` diffère `unordered_map`:  
  
-   Le `erase`, `bucket`, `bucket_count`, et `bucket_size` méthodes sont nommés `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, et `unsafe_bucket_size`, respectivement. Le `unsafe_` convention d’affectation de noms indique que ces méthodes ne sont pas compatibles avec la concurrence. Pour plus d’informations sur la sécurité d’accès concurrentiel, consultez [des opérations d’accès concurrentiel-Safe](#map-safety).  
  
-   Opérations d’insertion n’invalident pas les pointeurs ou itérateurs existants, ni de leur évolution l’ordre des éléments qui existent déjà dans la carte. Insérer et de parcourir les opérations se déroulent simultanément.  
  
-   `concurrent_unordered_map` prend en charge transférer itération uniquement.  
  
-   Insertion de ne pas invalider ou mettre à jour les itérateurs qui sont retournés par `equal_range`. Insertion peut ajouter des éléments inégaux à la fin de la plage. Un élément égal pointe l’itérateur de début.  
  
 Pour aider à éviter un blocage, aucune méthode de `concurrent_unordered_map` maintient un verrou lorsqu’il appelle l’allocateur de mémoire, des fonctions de hachage ou autre code défini par l’utilisateur. En outre, vous devez vous assurer que la fonction de hachage évalue toujours les clés égales à la même valeur. Les meilleures fonctions de hachage distribuent uniformément les clés dans l’espace de code de hachage.  
  
###  <a name="map-safety"></a> Opérations d’accès concurrentiel sécurisé  
 Le `concurrent_unordered_map` classe permet les opérations d’insertion et d’accès à l’élément de concurrentiel. Opérations d’insertion n’invalident pas les pointeurs ou itérateurs existants. Itérateur d’accès et parcours opérations est également concurrentiel. Le tableau suivant présente les couramment utilisés `concurrent_unordered_map` méthodes et opérateurs sont concurrentiel.  
  
|||||  
|-|-|-|-|  
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|  
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|  
  
 Bien que le `count` méthode peut être appelée en toute sécurité à partir de threads en cours d’exécution simultanément, différents threads peuvent recevoir des résultats différents si une nouvelle valeur est simultanément insérée dans le conteneur.  
  
 Le tableau suivant montre les méthodes couramment utilisées et les opérateurs qui ne sont pas compatibles avec la concurrence.  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq) 


  
 Outre ces méthodes, toute méthode qui commence par `unsafe_` n’est pas aussi concurrentiel.  
  
 [[Haut](#top)]  
  
##  <a name="unordered_multimap"></a> concurrent_unordered_multimap, classe  
 Le [concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) classe ressemble étroitement à la `concurrent_unordered_map` , sauf qu’elle autorise les valeurs multiples mapper à la même clé de classe. Elle diffère également de `concurrent_unordered_map` comme suit :  
  
-   Le [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) méthode retourne un itérateur au lieu de `std::pair<iterator, bool>`.  

  
-   Le `concurrent_unordered_multimap` ne fournit pas de classe `operator[]` ni le `at` (méthode).  
  
 L’exemple suivant montre la structure de base pour l’utilisation de `concurrent_unordered_multimap`. Cet exemple insère des touches de caractère dans la plage ['a', ' i']. `concurrent_unordered_multimap` permet à une clé pour avoir plusieurs valeurs.  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]  
  
 [[Haut](#top)]  
  
##  <a name="unordered_set"></a> concurrent_unordered_set, classe  
 Le [concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) classe ressemble étroitement à la `concurrent_unordered_map` classe, à ceci près qu’il gère des valeurs au lieu de paires clé / valeur. Le `concurrent_unordered_set` ne fournit pas de classe `operator[]` ni le `at` (méthode).  
  
 L’exemple suivant montre la structure de base pour l’utilisation de `concurrent_unordered_set`. Cet exemple insère des valeurs de caractère dans la plage ['a', ' i']. Il est possible d’effectuer des insertions en parallèle.  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]  
  
 [[Haut](#top)]  
  
##  <a name="unordered_multiset"></a> concurrent_unordered_multiset, classe  
 Le [concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) classe ressemble étroitement à la `concurrent_unordered_set` classe, à ceci près qu’il autorise les valeurs en double. Elle diffère également de `concurrent_unordered_set` comme suit :  
  

-   Le [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) méthode retourne un itérateur au lieu de `std::pair<iterator, bool>`.  

  
-   Le `concurrent_unordered_multiset` ne fournit pas de classe `operator[]` ni le `at` (méthode).  
  
 L’exemple suivant montre la structure de base pour l’utilisation de `concurrent_unordered_multiset`. Cet exemple insère des valeurs de caractère dans la plage ['a', ' i']. `concurrent_unordered_multiset` permet à une valeur à se produire plusieurs fois.  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]  
  
 [[Haut](#top)]  
  
##  <a name="combinable"></a> combinable, classe  
 Le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe fournit un stockage local des threads réutilisable qui vous permet d’effectuer des calculs affinés puis de fusionner ces calculs dans un résultat final. Vous pouvez considérer un objet `combinable` comme une variable de réduction.  
  
 Le `combinable` classe est utile lorsque vous avez une ressource qui est partagée entre plusieurs threads ou tâches. Le `combinable` classe vous permet d’éliminer l’état partagé en fournissant l’accès aux ressources partagées sans verrou. Par conséquent, cette classe fournit une alternative à l’aide d’un mécanisme de synchronisation, par exemple, un mutex, pour synchroniser l’accès aux données partagées à partir de plusieurs threads.  
  
###  <a name="combinable-features"></a> Méthodes et fonctionnalités  
 Le tableau suivant présente certaines des méthodes importantes de la `combinable` classe. Pour plus d’informations sur tous les `combinable` méthodes de la classe, consultez [combinable, classe](../../parallel/concrt/reference/combinable-class.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[local](reference/combinable-class.md#local)|Récupère une référence à la variable locale qui est associée avec le contexte actuel du thread.|  
|[clear](reference/combinable-class.md#clear)|Supprime toutes les variables locales de thread à partir de la `combinable` objet.|  
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Utilise la fonction combine fournie pour générer une valeur finale à partir de l’ensemble de tous les calculs de thread local.|  
  
 Le `combinable` classe est une classe de modèle qui est paramétrée sur le résultat fusionné final. Si vous appelez le constructeur par défaut, le `T` type de paramètre de modèle doit avoir un constructeur par défaut et un constructeur de copie. Si le `T` type de paramètre de modèle n’a pas un constructeur par défaut, appelez la version surchargée du constructeur qui prend une fonction d’initialisation en tant que paramètre.  
  
 Vous pouvez stocker des données supplémentaires dans un `combinable` objet une fois que vous appelez le [combiner](reference/combinable-class.md#combine) ou [combine_each](reference/combinable-class.md#combine_each) méthodes. Vous pouvez également appeler le `combine` et `combine_each` plusieurs fois. Si aucune valeur locale dans un `combinable` l’objet de modifications, la `combine` et `combine_each` méthodes produisent le même résultat chaque fois qu’elles sont appelées.  
  
###  <a name="combinable-examples"></a> Exemples  
 Pour obtenir des exemples sur l’utilisation du `combinable` de classe, consultez les rubriques suivantes :  
  
-   [Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [Guide pratique pour utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[Haut](#top)]  
  
## <a name="related-topics"></a>Rubriques connexes  
 [Guide pratique pour utiliser des conteneurs parallèles pour une efficacité accrue](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 Montre comment utiliser des conteneurs parallèles pour stocker efficacement et accéder aux données en parallèle.  
  
 [Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 Montre comment utiliser le `combinable` classe pour éliminer l’état partagé et ainsi améliorer les performances.  
  
 [Guide pratique pour utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 Montre comment utiliser un `combine` fonction pour fusionner des jeux de données locales de thread.  
  
 [Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 Décrit la bibliothèque PPL, qui fournit un modèle de programmation impérative qui favorise l’évolutivité et la facilité d’utilisation pour le développement d’applications simultanées.  
  
## <a name="reference"></a>Référence  
 [concurrent_vector, classe](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue, classe](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map, classe](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap, classe](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set, classe](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset, classe](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable, classe](../../parallel/concrt/reference/combinable-class.md)
