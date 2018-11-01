---
title: system_clock, structure
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 66710f94d96f069d6d388d6b49c76747c618a0d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557987"
---
# <a name="systemclock-structure"></a>system_clock, structure

Représente un *type d’horloge* basé sur l’horloge en temps réel du système.

## <a name="syntax"></a>Syntaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Notes

Un *type d’horloge* est utilisé pour obtenir l’heure actuelle au format UTC. Le type exprime une instanciation de la classe [duration](../standard-library/duration-class.md) et le modèle de classe [time_point](../standard-library/time-point-class.md), et il définit une fonction membre statique `now()` qui retourne l’heure.

Une horloge est *monotone* si la valeur retournée par un premier appel à `now()` est toujours inférieure ou égale à la valeur retournée par un appel ultérieur à `now()`.

Une horloge est *stable* si elle est *monotone* et si le laps de temps entre les battements d’horloge est constant.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`system_clock::duration`|Synonyme de `duration<rep, period>`.|
|`system_clock::period`|Synonyme du type qui est utilisé pour représenter le cycle d'horloge dans l'instanciation contenue de `duration`.|
|`system_clock::rep`|Synonyme du type qui est utilisé pour représenter le nombre de battements d'horloge dans l'instanciation contenue de `duration`.|
|`system_clock::time_point`|Synonyme de `time_point<Clock, duration>`, où `Clock` est un synonyme du type d'horloge ou d'un autre type d'horloge basé sur la même époque et ayant le même type `duration` imbriqué.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|----------|-----------------|
|[from_time_t](#from_time_t)|Static. Retourne un `time_point` qui se rapproche le plus d'une heure spécifiée.|
|[maintenant](#now)|Static. Retourne l'heure actuelle.|
|[to_time_t](#to_time_t)|Static. Retourne un objet `time_t` qui se rapproche le plus d'un `time_point` spécifié.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[system_clock::is_monotonic, constante](#is_monotonic_constant)|Spécifie si le type d'horloge est monotone.|
|[system_clock::is_steady, constante](#is_steady_constant)|Spécifie si le type d'horloge est stable.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t

Méthode statique qui retourne un [time_point](../standard-library/time-point-class.md) qui se rapproche le temps qui est représenté par *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Paramètres

*TM*<br/>
Objet [time_t](../c-runtime-library/standard-types.md).

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic, constante

Valeur statique qui spécifie si le type d’horloge est monotone.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Valeur de retour

Dans cette implémentation, `system_clock::is_monotonic` retourne toujours **false**.

### <a name="remarks"></a>Notes

Une horloge est *monotone* si la valeur retournée par un premier appel à `now()` est toujours inférieure ou égale à la valeur retournée par un appel ultérieur à `now()`.

## <a name="is_steady_constant"></a>  system_clock::is_steady, constante

Valeur statique qui spécifie si le type d’horloge est *stable*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Valeur de retour

Dans cette implémentation, `system_clock::is_steady` retourne toujours **false**.

### <a name="remarks"></a>Notes

Une horloge est *stable* si elle est [monotone](#is_monotonic_constant) et si le laps de temps entre les battements d’horloge est constant.

## <a name="now"></a>  system_clock::now

Méthode statique qui retourne l’heure actuelle.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Objet [time_point](../standard-library/time-point-class.md) qui représente l’heure actuelle.

## <a name="to_time_t"></a>  system_clock::to_time_t

Méthode statique qui retourne un [time_t](../c-runtime-library/standard-types.md) qui se rapproche le temps qui est représenté par *temps*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Paramètres

*Heure*<br/>
Objet [time_point](../standard-library/time-point-class.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[steady_clock, struct](../standard-library/steady-clock-struct.md)<br/>
