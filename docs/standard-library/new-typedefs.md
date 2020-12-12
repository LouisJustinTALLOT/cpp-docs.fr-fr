---
description: 'En savoir plus sur : &lt; nouveaux &gt; typedefs'
title: '&lt;new&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 0c8e73f10b8429d2c55805c017dded98843af9f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338168"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt;, typedefs

## <a name="hardware_constructive_interference_size"></a><a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Notes

Ce nombre correspond à la taille maximale recommandée de la mémoire contiguë occupée par deux objets accessibles avec la localité temporelle par des threads simultanés. Elle doit être au moins égale à `alignof(max_align_t)` .

### <a name="example"></a>Exemple

```cpp
struct together {
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a><a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Notes

Ce nombre est le décalage minimal recommandé entre deux objets faisant l’objet d’un accès simultané pour éviter une dégradation des performances supplémentaire en raison de la contention introduite par l’implémentation. Elle doit être au moins égale à `alignof(max_align_t)` .

### <a name="example"></a>Exemple

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a><a name="new_handler"></a> new_handler

Le type pointe vers une fonction pouvant être utilisée comme gestionnaire new.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Notes

Ce type de fonction de gestionnaire est appelé par l' **opérateur New** ou `operator new[]` lorsqu’il ne peut pas répondre à une demande de stockage supplémentaire.

### <a name="example"></a>Exemple

Pour obtenir un exemple utilisant `new_handler` comme valeur de retour, consultez [set_new_handler](../standard-library/new-functions.md#set_new_handler).
