---
description: 'En savoir plus sur : structure duration_values'
title: duration_values, structure
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: 9bf784b0976a06c6d395498084508251d9ebd4bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324473"
---
# <a name="duration_values-structure"></a>duration_values, structure

Fournit des valeurs spécifiques pour le paramètre de modèle [duration](../standard-library/duration-class.md)`Rep`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[max](#max)|Statique. Spécifie la limite supérieure pour une valeur de type `Rep`.|
|[min](#min)|Statique. Spécifie la limite inférieure pour une valeur de type `Rep`.|
|[nuls](#zero)|Statique. Retourne `Rep(0)`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<chrono>

**Espace de noms :** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a> duration_values :: max

Méthode statique qui retourne la limite supérieure des valeurs de type `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être supérieure à [duration_values::zero](#zero).

## <a name="duration_valuesmin"></a><a name="min"></a> duration_values :: min

Méthode statique qui retourne la limite inférieure des valeurs de type `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être inférieure ou égale à [duration_values::zero](#zero).

## <a name="duration_valueszero"></a><a name="zero"></a> duration_values :: Zero

Retourne `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l'utilisateur, la valeur de retour doit représenter l'infini additif.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
