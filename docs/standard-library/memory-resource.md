---
description: 'En savoir plus sur : &lt; memory_resource&gt;'
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: d575d94323552fd75fb6217ced7933e5050ee8b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183800"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource&gt;

Définit le memory_resource de modèle de classe de conteneur et ses modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory_resource>
```

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur ! =](../standard-library/memory-resource-operators.md#op_neq)|Teste si l’objet memory_resource situé à gauche de l’opérateur n’est pas égal à l’objet memory_resource situé à droite.|
|[opérateur = =](../standard-library/memory-resource-operators.md#op_eq_eq)|Teste si l’objet memory_resource situé à gauche de l’opérateur est égal à l’objet memory_resource situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Nom|Description|
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Classes et structs

|Nom|Description|
|-|-|
|[Classe memory_resource](../standard-library/memory-resource-class.md)||
|[Classe monotonic_buffer_resource](../standard-library/monotonic-buffer-resource-class.md)||
|[Struct pool_options](../standard-library/pool-options-structure.md)||
|[Classe synchronized_pool_resource](../standard-library/synchronized-pool-resource-class.md)||
|[Classe unsynchronized_pool_resource](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
