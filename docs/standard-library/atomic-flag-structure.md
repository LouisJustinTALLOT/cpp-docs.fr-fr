---
title: atomic_flag, structure
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 36944c3c3bdc58272d87bbcdfb119d1c52c43995
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447404"
---
# <a name="atomicflag-structure"></a>atomic_flag, structure

Décrit un objet qui définit et efface atomiquement un indicateur **bool** . Les opérations sur les indicateurs atomiques sont toujours sans verrou.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[clear](#clear)|Définit l’indicateur stocké sur false.|
|[test_and_set](#test_and_set)|Définit l’indicateur stocké sur **true** et retourne la valeur de l’indicateur initial.|

## <a name="remarks"></a>Notes

Les objets `atomic_flag` peuvent être passés aux fonctions non-membres [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) et [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Ils peuvent être initialisés à l’aide de la valeur `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> atomiques

**Espace de noms :** std

## <a name="clear"></a>  atomic_flag::clear

Définit l’indicateur **bool** qui est stocké `*this` dans sur **false**, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ordre*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set

Affecte à l’indicateur **bool** stocké dans `*this` la **valeur true**, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ordre*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur initiale de l’indicateur est stockée dans `*this`.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)
