---
title: '&lt;memory&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
dev_langs:
- C++
helpviewer_keywords:
- memory header
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b90a96816855e08610d0f63f3ab5c237d564453
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217947"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

Définit une classe, un opérateur et plusieurs modèles qui aident à allouer et libérer des objets.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory>

```

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|Obtient l'adresse exacte d'un objet.|
|[align](../standard-library/memory-functions.md#align)|Retourne un pointeur vers une plage d'une taille donnée, en fonction de l'alignement et de l'adresse de départ.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Crée un `shared_ptr` aux objets qui sont alloués et construits pour un type donné avec un allocateur spécifié.|
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Cast de type const vers `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informe un récupérateur de mémoire que les caractères à partir d'une adresse spécifiée et compris dans la taille de bloc indiquée ne contiennent aucun pointeur traçable.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informe une opération garbage collection que l’adresse indiquée est dédiée au stockage alloué et est accessible.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Supprime les objets alloués avec `operator new`. Fonction pouvant être utilisée avec `unique_ptr`.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Cast dynamique vers `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Obtient une suppression à partir de `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Retourne le type de sécurité de pointeur supposé par tout récupérateur de mémoire.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Alloue un stockage temporaire pour une séquence d'éléments qui ne dépasse pas un nombre spécifié d'éléments.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Crée et retourne un objet `shared_ptr` qui pointe vers l'objet alloué construit de zéro ou de plusieurs arguments à l'aide de l'allocateur par défaut.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Crée et retourne un objet [unique_ptr](../standard-library/unique-ptr-class.md) qui pointe vers l’objet alloué construit à partir de zéro, un ou plusieurs arguments.|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Permet des comparaisons mixtes basées sur la propriété de pointeurs partagés et faibles.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Énumération de toutes les valeurs de retour possibles pour `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Libère la mémoire temporaire allouée à l'aide de la fonction de modèle `get_temporary_buffer`.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Cast statique vers `shared_ptr`.|
|[swap](../standard-library/memory-functions.md#swap)|Échanger deux objets `shared_ptr` ou `weak_ptr`.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d'adresse de base et une taille de bloc peuvent maintenant contenir des pointeurs traçables.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informe un objet `garbage_collector` qu'un emplacement de mémoire spécifié n'est pas accessible.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Copie les objets à partir d'une plage d'entrée spécifiée dans une plage de destination non initialisée.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Crée une copie d'un nombre spécifié d'éléments à partir d'un itérateur d'entrée. Les copies sont placées dans un itérateur forward.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Copie les objets d'une valeur spécifiée dans une plage de destination non initialisée.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Copie les objets d'une valeur spécifiée dans un nombre spécifié d'éléments d'une plage de destination non initialisée.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Vérifie si un objet allocateur est supérieur ou égal à un second objet allocateur d'une classe donnée.|
|[operator<](../standard-library/memory-operators.md#op_lt)|Vérifie si un objet est inférieur à un second objet d'une classe donnée.|
|[operator\<=](../standard-library/memory-operators.md#op_gt_eq)|Vérifie si un objet est inférieur ou égal à un second objet d'une classe donnée.|
|[operator>](../standard-library/memory-operators.md#op_gt)|Vérifie si un objet est supérieur à un second objet d'une classe donnée.|
|[operator<<](../standard-library/memory-operators.md#op_lt_lt)|Outil d'insertion `shared_ptr`.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[allocator](../standard-library/allocator-class.md)|Cette classe de modèle décrit un objet qui gère l’allocation et la libération de stockage pour des tableaux d’objets de type **Type**.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Décrit un objet qui détermine toutes les informations qui sont requises par un conteneur activé par allocateur.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|La classe de modèle décrit un objet qui stocke un pointeur vers un objet alloué du type **Type** <strong>\*</strong> qui garantit que l’objet vers lequel il pointe est supprimé lorsque son auto_ptr englobant Obtient détruit.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Signale une exception weak_ptr incorrecte.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Aide à générer un `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Fournit les informations requises par un objet de la classe de modèle `allocator_traits` pour décrire un allocateur avec le type pointeur `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Classe d'adaptateur fournie pour permettre aux algorithmes de stocker leurs résultats dans la mémoire non initialisée.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Encapsule un pointeur intelligent contenant des références autour d'un objet alloué dynamiquement.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Stocke un pointeur vers un objet détenu. Le pointeur n'est détenu par aucun autre `unique_ptr`. L'objet `unique_ptr` est détruit lorsque le propriétaire est détruit.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Encapsule un pointeur faiblement lié.|

### <a name="specializations"></a>Spécialisations

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|Spécialisation de l'allocateur de classe de modèle en type void, définissant les seuls types de membres qui sont pertinents dans ce contexte spécialisé.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
