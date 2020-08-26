---
title: '&lt;memory&gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 0e3ce4a4411bd6d4c352802a96c97e93c66491df
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836463"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

Définit une classe, un opérateur et plusieurs modèles qui aident à allouer et libérer des objets.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<memory>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[AddressOf](../standard-library/memory-functions.md#addressof)|Obtient l'adresse exacte d'un objet.|
|[align](../standard-library/memory-functions.md#align)|Retourne un pointeur vers une plage d'une taille donnée, en fonction de l'alignement et de l'adresse de départ.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Crée un `shared_ptr` objet aux objets qui sont alloués et construits pour un type donné avec un allocateur spécifié.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Cast de type const vers `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informe un récupérateur de mémoire que les caractères à partir d'une adresse spécifiée et compris dans la taille de bloc indiquée ne contiennent aucun pointeur traçable.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informe une opération garbage collection que l’adresse indiquée est dédiée au stockage alloué et est accessible.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Supprime les objets alloués avec `operator new`. Fonction pouvant être utilisée avec `unique_ptr`.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|`destroy`Méthode sténographique.|
|[suppression](../standard-library/memory-functions.md#destroy)|`destroy`Méthode sténographique.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|`destroy`Méthode sténographique.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Cast dynamique vers `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Obtient une suppression à partir de `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Retourne le type de sécurité de pointeur supposé par tout récupérateur de mémoire.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Alloue un stockage temporaire pour une séquence d'éléments qui ne dépasse pas un nombre spécifié d'éléments.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Crée et retourne un objet `shared_ptr` qui pointe vers l'objet alloué construit de zéro ou de plusieurs arguments à l'aide de l'allocateur par défaut.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Crée et retourne un objet [unique_ptr](../standard-library/unique-ptr-class.md) qui pointe vers l’objet alloué construit à partir de zéro, un ou plusieurs arguments.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Énumération de toutes les valeurs de retour possibles pour `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Libère la mémoire temporaire allouée à l'aide de la fonction de modèle `get_temporary_buffer`.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Cast statique vers `shared_ptr`.|
|[swap](../standard-library/memory-functions.md#swap)|Échanger deux objets `shared_ptr` ou `weak_ptr`.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d'adresse de base et une taille de bloc peuvent maintenant contenir des pointeurs traçables.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informe un objet `garbage_collector` qu'un emplacement de mémoire spécifié n'est pas accessible.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Copie les objets à partir d'une plage d'entrée spécifiée dans une plage de destination non initialisée.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Crée une copie d'un nombre spécifié d'éléments à partir d'un itérateur d'entrée. Les copies sont placées dans un itérateur vers l’avant.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|`uninitialized_default_construct`Méthode sténographique.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|`uninitialized_construct`Méthode sténographique.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Copie les objets d'une valeur spécifiée dans une plage de destination non initialisée.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Copie les objets d'une valeur spécifiée dans un nombre spécifié d'éléments d'une plage de destination non initialisée.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|`uninitialized_move`Méthode sténographique.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|`uninitialized_move`Méthode sténographique.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|`uninitialized_value_construct`Méthode sténographique.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|`uninitialized_value_construct`Méthode sténographique.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur ! =](../standard-library/memory-operators.md#op_neq)|Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.|
|[opérateur = =](../standard-library/memory-operators.md#op_eq_eq)|Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.|
|[>opérateur =](../standard-library/memory-operators.md#op_gt_eq)|Vérifie si un objet allocateur est supérieur ou égal à un second objet allocateur d'une classe donnée.|
|[<d’opérateur ](../standard-library/memory-operators.md#op_lt)|Vérifie si un objet est inférieur à un second objet d'une classe donnée.|
|[and\<=](../standard-library/memory-operators.md#op_gt_eq)|Vérifie si un objet est inférieur ou égal à un second objet d'une classe donnée.|
|[>d’opérateur ](../standard-library/memory-operators.md#op_gt)|Vérifie si un objet est supérieur à un second objet d'une classe donnée.|
|[<<d’opérateur ](../standard-library/memory-operators.md#op_lt_lt)|Outil d'insertion `shared_ptr`.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[allocator](../standard-library/allocator-class.md)|Le modèle de classe décrit un objet qui gère l’allocation et la libération de stockage pour des tableaux d’objets de type **type**.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Décrit un objet qui détermine toutes les informations qui sont requises par un conteneur activé par allocateur.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Le modèle de classe décrit un objet qui stocke un pointeur vers un objet alloué de **type type** <strong>\*</strong> qui garantit que l’objet vers lequel il pointe est supprimé lorsque son auto_ptr englobant est détruit.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Signale une exception weak_ptr incorrecte.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Aide à générer un `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Fournit les informations nécessaires à un objet de type `allocator_traits` pour décrire un allocateur avec le type pointeur `Ptr` .|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Classe d'adaptateur fournie pour permettre aux algorithmes de stocker leurs résultats dans la mémoire non initialisée.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Encapsule un pointeur intelligent contenant des références autour d'un objet alloué dynamiquement.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Stocke un pointeur vers un objet détenu. Le pointeur n'est détenu par aucun autre `unique_ptr`. L'objet `unique_ptr` est détruit lorsque le propriétaire est détruit.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Encapsule un pointeur faiblement lié.|

### <a name="structures"></a>Structures

|Nom|Description|
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|Hachage|Fournit des surcharges spécialisées pour `unique_ptr` et `shared_ptr` .|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Permet des comparaisons mixtes basées sur la propriété de pointeurs partagés et faibles.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Spécialisations

|Nom|Description|
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|Spécialisation de l’allocateur de modèle de classe en type **`void`** , définissant uniquement les types de membres qui ont un sens dans ce contexte spécialisé.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
