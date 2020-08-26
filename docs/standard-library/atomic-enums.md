---
title: '&lt;atomic&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: d8a4e9196e27933c75a32c256114e968b55678a6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834893"
---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt;, énumérations

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a> Énumération memory_order

Fournit les noms symboliques des opérations de synchronisation sur les emplacements de mémoire. Ces opérations affectent l’affichage des assignations d’un thread dans un autre thread.

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Membres de l’énumération

|Nom|Description|
|-|-|
|`memory_order_relaxed`|Aucun ordre nécessaire.|
|`memory_order_consume`|Une opération de chargement agit comme une opération de consommation sur l’emplacement de mémoire.|
|`memory_order_acquire`|Une opération de chargement agit comme une opération d’acquisition sur l’emplacement de mémoire.|
|`memory_order_release`|Une opération de stockage agit comme une opération de libération sur l’emplacement de mémoire.|
|`memory_order_acq_rel`|Combine `memory_order_acquire` et `memory_order_release`.|
|`memory_order_seq_cst`|Combine `memory_order_acquire` et `memory_order_release`. Les accès à la mémoire marqués comme `memory_order_seq_cst` doivent être cohérents de façon séquentielle.|

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)
