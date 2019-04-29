---
title: atomic_flag, structure
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 13af0c26b765aa7ebbbd1ec22b5a0ed1b8cce0ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377255"
---
# <a name="atomicflag-structure"></a>atomic_flag, structure

Décrit un objet qui définit et efface atomiquement un **bool** indicateur. Les opérations sur les indicateurs atomiques sont toujours sans verrou.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[clear](#clear)|Définit l’indicateur stockée avec **false**.|
|[test_and_set](#test_and_set)|Définit l’indicateur stockée avec **true** et retourne la valeur d’indicateur initial.|

## <a name="remarks"></a>Notes

Les objets `atomic_flag` peuvent être passés aux fonctions non-membres [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) et [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Ils peuvent être initialisés à l’aide de la valeur `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<atomic >

**Espace de noms :** std

## <a name="clear"></a>  atomic_flag::clear

Définit le **bool** indicateur qui est stocké dans `*this` à **false**, dans le texte spécifié [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Order*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set

Définit le **bool** indicateur qui est stocké dans `*this` à **true**, dans le texte spécifié [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Paramètres

*Order*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur initiale de l’indicateur est stockée dans `*this`.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)<br/>
