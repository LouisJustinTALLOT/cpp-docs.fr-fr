---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269341"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Définit le memory_resource de classe de modèle de conteneur et ses modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory_resource>
```

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[!=, opérateur](../standard-library/memory-resource-operators.md#op_neq)|Teste si l’objet memory_resource sur le côté gauche de l’opérateur n’est pas égal à l’objet memory_resource sur le côté droit.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Teste si l’objet memory_resource sur le côté gauche de l’opérateur est égal à l’objet memory_resource sur le côté droit.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Fonctions

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|[memory_resource, classe](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource, classe](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options Struct](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource, classe](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource, classe](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
