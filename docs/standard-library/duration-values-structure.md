---
title: duration_values, structure
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368742"
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
|[Max](#max)|Statique. Spécifie la limite supérieure pour une valeur de type `Rep`.|
|[Min](#min)|Statique. Spécifie la limite inférieure pour une valeur de type `Rep`.|
|[Zéro](#zero)|Statique. Retourne `Rep(0)`.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<chrono>

**Espace de noms :** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values::max

Méthode statique qui retourne la limite supérieure des valeurs de type `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valeur de retour

Retourne `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être supérieure à [duration_values::zero](#zero).

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values::min

Méthode statique qui retourne la limite inférieure des valeurs de type `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valeur de retour

Retourne `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être inférieure ou égale à [duration_values::zero](#zero).

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values::zéro

Retourne `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l'utilisateur, la valeur de retour doit représenter l'infini additif.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
