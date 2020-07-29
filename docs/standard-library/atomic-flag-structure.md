---
title: atomic_flag, structure
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ff60e05c7d14104e164e8251a9146f8b0d0dcde3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203921"
---
# <a name="atomic_flag-structure"></a>atomic_flag, structure

Décrit un objet qui définit et efface atomiquement un **`bool`** indicateur. Les opérations sur les indicateurs atomiques sont toujours sans verrou.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[clear](#clear)|Affecte la valeur à l’indicateur stocké **`false`** .|
|[test_and_set](#test_and_set)|Définit l’indicateur stocké sur **`true`** et retourne la valeur de l’indicateur initial.|

## <a name="remarks"></a>Notes

Les objets `atomic_flag` peuvent être passés aux fonctions non-membres [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) et [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Ils peuvent être initialisés à l’aide de la valeur `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Spécifications

**En-tête :**\<atomic>

**Espace de noms :** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag :: Clear

Définit l' **`bool`** indicateur stocké dans dans **`*this`** **`false`** , dans les contraintes de [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ordre*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag :: test_and_set

Définit l' **`bool`** indicateur stocké dans dans **`*this`** **`true`** , dans les contraintes de [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ordre*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur initiale de l’indicateur stocké dans **`*this`** .

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)
