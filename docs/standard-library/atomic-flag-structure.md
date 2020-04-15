---
title: atomic_flag, structure
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376869"
---
# <a name="atomic_flag-structure"></a>atomic_flag, structure

Décrit un objet qui fixe et efface atomiquement un drapeau **bool.** Les opérations sur les indicateurs atomiques sont toujours sans verrou.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Clair](#clear)|Définit le drapeau stocké à **faux**.|
|[test_and_set](#test_and_set)|Définit le drapeau stocké pour **vrai** et retourne la valeur initiale du drapeau.|

## <a name="remarks"></a>Notes

Les objets `atomic_flag` peuvent être passés aux fonctions non-membres [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) et [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Ils peuvent être initialisés à l’aide de la valeur `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Spécifications

**En-tête:** \<> atomique

**Espace de noms :** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::clair

Définit le drapeau **bool** `*this` qui est stocké dans **faux**, dans les contraintes [spécifiées memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag::test_and_set

Définit le drapeau **bool** `*this` qui est stocké dans **vrai,** dans les contraintes [spécifiées memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur initiale de l’indicateur est stockée dans `*this`.

## <a name="see-also"></a>Voir aussi

[\<>atomique](../standard-library/atomic.md)
