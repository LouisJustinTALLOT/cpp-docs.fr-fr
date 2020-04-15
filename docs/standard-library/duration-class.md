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
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368752"
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
|[Durée](#duration)|Construit un objet `duration`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[count](#count)|Retourne le nombre de battements d’horloge dans l’intervalle de temps.|
|[Max](#max)|Statique. Retourne la valeur maximale autorisée du paramètre de modèle `Ref`.|
|[Min](#min)|Statique. Retourne la valeur minimale autorisée du paramètre de modèle `Ref`.|
|[Zéro](#zero)|Statique. Retourne `Rep`(0).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[durée::opérateur-](#operator-)|Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.|
|[durée::opérateur--](#operator--)|Décrémente le nombre de battements stocké.|
|[durée::opérateur](#op_eq)|Réduit le nombre de battements stocké modulo une valeur spécifiée.|
|[duration::operator*=](#op_star_eq)|Multiplie le nombre de battements stocké par une valeur spécifiée.|
|[durée::opérateur/MD](#op_div_eq)|Divise le nombre de battements stocké par le nombre de battements d’un objet `duration` spécifié.|
|[durée::opérateur](#op_add)|Retourne `*this`.|
|[durée::opérateur](#op_add_add)|Incrémente le nombre de battements stocké.|
|[durée::opérateur](#op_add_eq)|Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.|
|[durée::opérateur-MD](#operator-_eq)|Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<chrono>

**Espace de noms :** std::chrono

## <a name="durationcount"></a><a name="count"></a>durée::comptez

Récupère le nombre de battements d'horloge dans l'intervalle de temps.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de battements d'horloge dans l'intervalle de temps.

## <a name="durationduration-constructor"></a><a name="duration"></a>durée::duration Constructor

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

*Période2*\
Spécialisation de modèle `std::ratio` pour représenter la période de battements en unités de secondes.

*R*\
Nombre de battements de la période par défaut.

*Dur Dur*\
Nombre de tiques de période spécifiées par *période 2*.

### <a name="remarks"></a>Notes

Le constructeur par défaut crée un objet qui n’est pas initialisé. L’initialisation de valeurs à l’aide d’accolades vides initialise un objet qui représente un intervalle de temps de zéro battement d’horloge.

Le second, un constructeur d’argument modèle construit un *R* objet qui représente un `std::ratio<1>`intervalle de temps de tiques d’horloge R en utilisant une période par défaut de . Pour éviter le 2ème tour du nombre de tiques, il est erroné de construire un objet `duration::rep` de durée à partir d’un type de représentation *Rep2* qui peut être traité comme un type de point flottant quand ne peut pas être traité comme un type de point flottant.

Le troisième, deux modèles de construction d’argument construit un objet qui représente un intervalle de temps dont la longueur est l’intervalle de temps qui est spécifié par *Dur*. Pour éviter la troncation du nombre de battements, il ne faut pas construire un objet de durée à partir d’un autre objet de durée dont le type est *incommensurable* avec le type cible.

Un type de durée `D1` est *incommensurable* avec un autre type de durée `D2` si `D2` ne peut pas être traité comme un type à virgule flottante et que [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) n’est pas égal à 1.

Sauf si *Rep2* est `rep` implicitement convertible à et `treat_as_floating_point<rep>` *est vrai* ou `treat_as_floating_point<Rep2>` *est faux*, le deuxième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

À moins qu’aucun dépassement ne soit induit dans la conversion et que `treat_as_floating_point<rep>`*contienne la valeur true*, ou que `ratio_divide<Period2, period>::den` soit égal à 1 et que `treat_as_floating_point<Rep2>`*contienne la valeur false*, le troisième constructeur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>durée::max

Méthode statique qui retourne la limite supérieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::max())`.

## <a name="durationmin"></a><a name="min"></a>durée::min

Méthode statique qui retourne la limite inférieure des valeurs du type de paramètre de modèle `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Valeur de retour

Retourne `duration(duration_values<rep>::min())`.

## <a name="durationoperator-"></a><a name="operator-"></a>durée::opérateur-

Retourne une copie de l’objet `duration` avec un nombre de battements négatifs.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>durée::opérateur--

Décrémente le nombre de battements stocké.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne `*this`.

La deuxième méthode retourne une copie de `*this` effectuée avant la décrémentation.

## <a name="durationoperator"></a><a name="op_eq"></a>durée::opérateur

Réduit le nombre de battements stocké modulo une valeur spécifiée.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Paramètres

*Div*\
Pour la première méthode, *Div* représente un nombre de tiques. Pour la deuxième méthode, `duration` *Div* est un objet qui contient un nombre de tiques.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’opération modulo effectuée.

## <a name="durationoperator"></a><a name="op_star_eq"></a>durée::opérateur

Multiplie le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Paramètres

*Mult*\
Valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la multiplication effectuée.

## <a name="durationoperator"></a><a name="op_div_eq"></a>durée::opérateur/MD

Divise le nombre de battements stocké par une valeur spécifiée.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Paramètres

*Div*\
Valeur du type spécifié par `duration::rep`.

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la division effectuée.

## <a name="durationoperator"></a><a name="op_add"></a>durée::opérateur

Retourne `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>durée::opérateur

Incrémente le nombre de battements stocké.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première méthode retourne `*this`.

La deuxième méthode retourne une copie de `*this` effectuée avant l’incrémentation.

## <a name="durationoperator"></a><a name="op_add_eq"></a>durée::opérateur

Ajoute le nombre de battements d’un objet `duration` spécifié au nombre de battements stocké.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur Dur*\
Objet `duration` .

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois l’addition effectuée.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>durée::opérateur-MD

Soustrait le nombre de battements d’un objet `duration` spécifié du nombre de battements stocké.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur Dur*\
Objet `duration` .

### <a name="return-value"></a>Valeur de retour

Objet `duration` une fois la soustraction effectuée.

## <a name="durationzero"></a><a name="zero"></a>durée::zéro

Retourne `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>durée::mod opérateur

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

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values, structure](../standard-library/duration-values-structure.md)
