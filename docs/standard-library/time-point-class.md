---
description: 'En savoir plus sur : classe time_point'
title: time_point, classe
ms.date: 03/27/2019
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
helpviewer_keywords:
- std::chrono [C++], time_point
ms.openlocfilehash: f9818c6ec3817608864fac0108d73666a0ef3bf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167277"
---
# <a name="time_point-class"></a>time_point, classe

Un `time_point` décrit un type qui représente un point dans le temps. Il contient un objet de type [duration](../standard-library/duration-class.md) qui stocke le temps écoulé depuis l’époque qui est représentée par l’argument de modèle `Clock`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`time_point::clock`|Synonyme du paramètre de modèle `Clock`.|
|`time_point::duration`|Synonyme du paramètre de modèle `Duration`.|
|`time_point::period`|Synonyme du nom de type imbriqué `duration::period`.|
|`time_point::rep`|Synonyme du nom de type imbriqué `duration::rep`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[time_point](#time_point)|Construit un objet `time_point`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[max](#max)|Spécifie la limite supérieure pour `time_point::ref`.|
|[min](#min)|Spécifie la limite inférieure pour `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Retourne la valeur `duration` stockée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[time_point :: Operator + =](#op_add_eq)|Ajoute une valeur spécifiée à la durée stockée.|
|[time_point::operator-=](#operator-_eq)|Soustrait une valeur spécifiée de la durée stockée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<chrono>

**Espace de noms :** std::chrono

## <a name="time_pointmax"></a><a name="max"></a> time_point :: max

Méthode statique qui retourne la limite supérieure des valeurs de type `time_point::ref`.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne `time_point(duration::max())`.

## <a name="time_pointmin"></a><a name="min"></a> time_point :: min

Méthode statique qui retourne la limite inférieure des valeurs de type `time_point::ref`.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne `time_point(duration::min())`.

## <a name="time_pointoperator"></a><a name="op_add_eq"></a> time_point :: Operator + =

Ajoute une valeur spécifiée à la valeur [duration](../standard-library/duration-class.md) stockée.

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur renvoyée

Objet `time_point` une fois l’addition effectuée.

## <a name="time_pointoperator-"></a><a name="operator-_eq"></a> time_point :: Operator-=

Soustrait une valeur spécifiée de la valeur [duration](../standard-library/duration-class.md) stockée.

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur renvoyée

Objet `time_point` une fois la soustraction effectuée.

## <a name="time_pointtime_point-constructor"></a><a name="time_point"></a> time_point :: time_point, constructeur

Construit un objet `time_point`.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet [duration](../standard-library/duration-class.md).

*PM*\
Objet `time_point`.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet dont la valeur `duration` stockée est égale à [duration::zero](../standard-library/duration-class.md#zero).

Le deuxième constructeur construit un objet dont la *valeur de durée* stockée est égale à. À moins que `is_convertible<Duration2, duration>` ne contienne la valeur true, le deuxième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

Le deuxième constructeur initialise sa valeur `duration` à l'aide de `Tp.time_since_epoch()`.

## <a name="time_pointtime_since_epoch"></a><a name="time_since_epoch"></a> time_point :: time_since_epoch

Récupère la valeur [duration](../standard-library/duration-class.md) stockée.

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
