---
title: duration, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs:
- C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: a4b85fd369e82ceab0a6b5255267e32d864eab67
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956864"
---
# <a name="duration-class"></a>duration, classe

Décrit un type contenant un *intervalle de temps*, qui est le temps écoulé entre deux points dans le temps.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Notes

L’argument de modèle `Rep` décrit le type utilisé pour contenir le nombre de battements d’horloge dans l’intervalle. L’argument de modèle `Period` est une instanciation du [rapport](../standard-library/ratio.md) qui décrit la taille de l’intervalle représenté par chaque battement.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|duration::period, typedef|Représente un synonyme du paramètre de modèle `Period`.|
|duration::rep, typedef|Représente un synonyme du paramètre de modèle `Rep`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[durée](#duration)|Construit un objet `duration`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[count](#count)|Retourne le nombre de battements d’horloge dans l’intervalle de temps.|
|[max](#max)|Static. Retourne la valeur maximale autorisée du paramètre de modèle `Ref`.|
|[min](#min)|Static. Retourne la valeur minimale autorisée du paramètre de modèle `Ref`.|
|[zéro](#zero)|Static. Retourne `Rep`(0).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[duration::operator-](#operator-)|Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.|
|[duration::operator--](#operator--)|Décrémente le nombre de battements stocké.|
|[duration::operator=](#op_eq)|Réduit le nombre de battements stocké modulo une valeur spécifiée.|
|[duration::operator*=](#op_star_eq)|Multiplie le nombre de battements stocké par une valeur spécifiée.|
|[duration::operator/=](#op_div_eq)|Divise le nombre de battements stocké par le nombre de battements d’un objet `duration` spécifié.|
|[duration::operator+](#op_add)|Retourne `*this`.|
|[duration::operator++](#op_add_add)|Incrémente le nombre de battements stocké.|
|[duration::operator+=](#op_add_eq)|Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.|
|[duration::operator-=](#operator-_eq)|Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="count"></a>  duration::count

Récupère le nombre de battements d'horloge dans l'intervalle de temps.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de battements d'horloge dans l'intervalle de temps.

## <a name="duration"></a>  duration::duration, constructeur

Construit un objet `duration`.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);


template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Paramètres

*Rep2* un type arithmétique pour représenter le nombre de graduations.

*Period2* A `std::ratio` spécialisation de modèle pour représenter la période de battements en unités de secondes.

*R* le nombre de graduations de la période par défaut.

*Durée* le nombre de graduations de la période spécifiée par *Period2*.

### <a name="remarks"></a>Notes

Le constructeur par défaut crée un objet qui n’est pas initialisé. L’initialisation de valeurs à l’aide d’accolades vides initialise un objet qui représente un intervalle de temps de zéro battement d’horloge.

La seconde, un argument de modèle constructeur construit un objet qui représente un intervalle de temps de *R* à l’aide d’une période de battements d’horloge `std::ratio<1>`. Pour éviter l’arrondi des nombres de battements, c’est une erreur pour construire un objet de durée à partir d’un type de représentation *Rep2* qui peut être traité comme un à virgule flottante type quand `duration::rep` ne peut pas être traité comme un type à virgule flottante.

La troisième, deux constructeur à argument modèle construit un objet qui représente un intervalle de temps dont la longueur est l’intervalle de temps spécifié par *durée*. Pour éviter la troncation du nombre de battements, il ne faut pas construire un objet de durée à partir d’un autre objet de durée dont le type est *incommensurable* avec le type cible.

Un type de durée `D1` est *incommensurable* avec un autre type de durée `D2` si `D2` ne peut pas être traité comme un type à virgule flottante et que [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) n’est pas égal à 1.

À moins que *Rep2* est implicitement convertible en `rep` et `treat_as_floating_point<rep>` *vaut* ou `treat_as_floating_point<Rep2>` *sa valeur est false*, le deuxième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

À moins qu’aucun dépassement ne soit induit dans la conversion et que `treat_as_floating_point<rep>`*contienne la valeur true*, ou que `ratio_divide<Period2, period>::den` soit égal à 1 et que `treat_as_floating_point<Rep2>`*contienne la valeur false*, le troisième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="max"></a>  duration::max

Méthode statique qui retourne la limite supérieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::max())`.

## <a name="min"></a>  duration::min

Méthode statique qui retourne la limite inférieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::min())`.

## <a name="duration__operator-"></a>  duration::operator-

Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  duration::operator--

Décrémente le nombre de battements stocké.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne `*this`.

La deuxième méthode retourne une copie de `*this` effectuée avant la décrémentation.

## <a name="op_eq"></a>  duration::operator=

Réduit le nombre de battements stocké modulo une valeur spécifiée.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Paramètres

*Div* pour la première méthode, *Div* représente un nombre de battements. Pour la deuxième méthode, *Div* est un `duration` objet qui contient un nombre de battements.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’opération modulo effectuée.

## <a name="op_star_eq"></a>  duration::operator*=

Multiplie le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Paramètres

*Mult* une valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la multiplication effectuée.

## <a name="op_div_eq"></a>  duration::operator/=

Divise le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Paramètres

*Div* une valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la division effectuée.

## <a name="op_add"></a>  duration::operator+

Retourne `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  duration::operator++

Incrémente le nombre de battements stocké.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne `*this`.

La deuxième méthode retourne une copie de `*this` effectuée avant l’incrémentation.

## <a name="op_add_eq"></a>  duration::operator+=

Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Durée* A `duration` objet.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’addition effectuée.

## <a name="duration__operator-_eq"></a>  duration::operator-=

Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Durée* A `duration` objet.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la soustraction effectuée.

## <a name="zero"></a>  duration::zero

Retourne `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  duration::operator mod=

Réduit le nombre de cycles stocké modulo Div ou Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Paramètres

*Div* diviseur, qui est un objet de durée ou une valeur qui représente des nombres de cycles.

### <a name="remarks"></a>Notes

La première fonction membre réduit le nombre de cycles stocké modulo Div et retourne *this. La deuxième fonction membre réduit le nombre de battements stocké modulo Div.count() et retourne \*this.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values, structure](../standard-library/duration-values-structure.md)<br/>
