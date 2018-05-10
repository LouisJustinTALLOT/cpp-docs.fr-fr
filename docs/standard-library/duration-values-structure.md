---
title: duration_values, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d781d04097b205750e7ac65529cfa8ad7b37f9c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="durationvalues-structure"></a>duration_values, structure

Fournit des valeurs spécifiques pour le paramètre de modèle [duration](../standard-library/duration-class.md) `Rep`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[max](#max)|Static. Spécifie la limite supérieure pour une valeur de type `Rep`.|
|[min](#min)|Static. Spécifie la limite inférieure pour une valeur de type `Rep`.|
|[Zéro](#zero)|Static. Retourne `Rep(0)`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="max"></a>  duration_values::max

Méthode statique qui retourne la limite supérieure des valeurs de type `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valeur de retour

Retourne `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être supérieure à [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min

Méthode statique qui retourne la limite inférieure des valeurs de type `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valeur de retour

Retourne `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l’utilisateur, la valeur de retour doit être inférieure ou égale à [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Retourne `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Notes

Quand `Rep` est un type défini par l'utilisateur, la valeur de retour doit représenter l'infini additif.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
