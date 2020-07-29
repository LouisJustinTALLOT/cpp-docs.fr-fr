---
title: duration, classe
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 454c03aeb1a4666543a28759d02405a512453ffc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217790"
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
|[duration](#duration)|Construit un objet `duration`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[count](#count)|Retourne le nombre de battements d’horloge dans l’intervalle de temps.|
|[max](#max)|Statique. Retourne la valeur maximale autorisée du paramètre de modèle `Ref`.|
|[min](#min)|Statique. Retourne la valeur minimale autorisée du paramètre de modèle `Ref`.|
|[nuls](#zero)|Statique. Retourne `Rep`(0).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Duration :: Operator-](#operator-)|Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.|
|[Duration :: Operator--](#operator--)|Décrémente le nombre de battements stocké.|
|[Duration :: Operator =](#op_eq)|Réduit le nombre de battements stocké modulo une valeur spécifiée.|
|[duration::operator*=](#op_star_eq)|Multiplie le nombre de battements stocké par une valeur spécifiée.|
|[Duration :: Operator/=](#op_div_eq)|Divise le nombre de battements stocké par le nombre de battements d’un objet `duration` spécifié.|
|[Duration :: Operator +](#op_add)|Retourne **`*this`** .|
|[Duration :: Operator + +](#op_add_add)|Incrémente le nombre de battements stocké.|
|[Duration :: Operator + =](#op_add_eq)|Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.|
|[Duration :: Operator-=](#operator-_eq)|Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<chrono>

**Espace de noms :** std::chrono

## <a name="durationcount"></a><a name="count"></a>Duration :: Count

Récupère le nombre de battements d'horloge dans l'intervalle de temps.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de battements d'horloge dans l'intervalle de temps.

## <a name="durationduration-constructor"></a><a name="duration"></a>Duration ::d constructeur figuration

Construit un objet `duration`.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Paramètres

*Rep2*\
Type arithmétique pour représenter le nombre de battements.

*Period2*\
Spécialisation de modèle `std::ratio` pour représenter la période de battements en unités de secondes.

*R*\
Nombre de battements de la période par défaut.

*Dur*\
Nombre de graduations de la période spécifiée par *Period2*.

### <a name="remarks"></a>Notes

Le constructeur par défaut crée un objet qui n’est pas initialisé. L’initialisation de valeurs à l’aide d’accolades vides initialise un objet qui représente un intervalle de temps de zéro battement d’horloge.

Le deuxième constructeur d’argument de modèle construit un objet qui représente un intervalle de temps de battements d’horloge *R* à l’aide d’une période par défaut de `std::ratio<1>` . Pour éviter l’arrondi des nombres de battements, il ne faut pas construire un objet de durée à partir d’un type de représentation *Rep2* qui peut être traité comme un type à virgule flottante quand `duration::rep` ne peut pas être traité comme un type à virgule flottante.

Le troisième constructeur d’argument de modèle construit un objet qui représente un intervalle de temps dont la longueur est l’intervalle de temps *spécifié par la durée.* Pour éviter la troncation du nombre de battements, il ne faut pas construire un objet de durée à partir d’un autre objet de durée dont le type est *incommensurable* avec le type cible.

Un type de durée `D1` est *incommensurable* avec un autre type de durée `D2` si `D2` ne peut pas être traité comme un type à virgule flottante et [ratio_divide \<D1::period, D2::period> :: type ::d](../standard-library/ratio.md) en n’est pas 1.

Sauf si *Rep2* est implicitement convertible en `rep` et qu' `treat_as_floating_point<rep>` il *contient true* ou qu' `treat_as_floating_point<Rep2>` il *contient false*, le deuxième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

À moins qu’aucun dépassement ne soit induit dans la conversion et que `treat_as_floating_point<rep>`*contienne la valeur true*, ou que `ratio_divide<Period2, period>::den` soit égal à 1 et que `treat_as_floating_point<Rep2>`*contienne la valeur false*, le troisième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>Duration :: max

Méthode statique qui retourne la limite supérieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::max())`.

## <a name="durationmin"></a><a name="min"></a>Duration :: min

Méthode statique qui retourne la limite inférieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::min())`.

## <a name="durationoperator-"></a><a name="operator-"></a>Duration :: Operator-

Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>Duration :: Operator--

Décrémente le nombre de battements stocké.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne **`*this`** .

La deuxième méthode retourne une copie de **`*this`** qui est effectuée avant la décrémentation.

## <a name="durationoperator"></a><a name="op_eq"></a>Duration :: Operator =

Réduit le nombre de battements stocké modulo une valeur spécifiée.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Paramètres

*Div*\
Pour la première méthode, *div* représente un nombre de cycles. Pour la deuxième méthode, *div* est un `duration` objet qui contient un nombre de cycles.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’opération modulo effectuée.

## <a name="durationoperator"></a><a name="op_star_eq"></a>Duration :: Operator * =

Multiplie le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Paramètres

*Mult*\
Valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la multiplication effectuée.

## <a name="durationoperator"></a><a name="op_div_eq"></a>Duration :: Operator/=

Divise le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Paramètres

*Div*\
Valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la division effectuée.

## <a name="durationoperator"></a><a name="op_add"></a>Duration :: Operator +

Retourne **`*this`** .

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>Duration :: Operator + +

Incrémente le nombre de battements stocké.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne **`*this`** .

La deuxième méthode retourne une copie de **`*this`** qui est effectuée avant l’incrémentation.

## <a name="durationoperator"></a><a name="op_add_eq"></a>Duration :: Operator + =

Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’addition effectuée.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>Duration :: Operator-=

Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la soustraction effectuée.

## <a name="durationzero"></a><a name="zero"></a>Durée :: zéro

Retourne `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>Duration :: Operator mod =

Réduit le nombre de cycles stocké modulo Div ou Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Paramètres

*Div*\
Diviseur, qui est un objet duration ou une valeur représentant le nombre de cycles.

### <a name="remarks"></a>Notes

La première fonction membre réduit le nombre de cycles stocké modulo Div et retourne *this. La deuxième fonction membre réduit le nombre de battements stocké modulo Div.count() et retourne \*this.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values, structure](../standard-library/duration-values-structure.md)
