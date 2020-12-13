---
description: 'En savoir plus sur : classe d’index'
title: index, classe
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 46b49a7e0f65f06ad64ed32367cdfe6f6ca5ed1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330050"
---
# <a name="index-class"></a>index, classe

Définit un vecteur d’index à *N* dimensions.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang, ou nombre de dimensions.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur d’index](#index_ctor)|Initialise une nouvelle instance de la classe `index`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur--](#operator--)|Décrémente chaque élément de l' `index` objet.|
|[opérateur% =](#operator_mod_eq)|Calcule le modulo (reste) de chaque élément de l' `index` objet lorsque cet élément est divisé par un nombre.|
|[opérateur * =](#operator_star_eq)|Multiplie chaque élément de l' `index` objet par un nombre.|
|[opérateur/=](#operator_div_eq)|Divise chaque élément de l' `index` objet par un nombre.|
|[index ::, opérateur\[\]](#operator_at)|Retourne l’élément qui se trouve à l’index spécifié.|
|[opérateur + +](#operator_add_add)|Incrémente chaque élément de l' `index` objet.|
|[opérateur + =](#operator_add_eq)|Ajoute le nombre spécifié à chaque élément de l' `index` objet.|
|[opérateur =](#operator_eq)|Copie le contenu de l’objet spécifié dans celui- `index` ci.|
|[opérateur =](#operator_-_eq)|Soustrait le nombre spécifié de chaque élément de l' `index` objet.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Stocke le rang de l' `index` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`index`

## <a name="remarks"></a>Notes

La `index` structure représente un vecteur de coordonnées de *n* entiers qui spécifie une position unique dans un espace à *n* dimensions. Les valeurs du vecteur sont triées du plus significatif au moins significatif. Vous pouvez récupérer les valeurs des composants à l’aide de [Operator =](#operator_eq).

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="index-constructor"></a><a name="index_ctor"></a> Constructeur d’index

Initialise une nouvelle instance de la classe d’index.

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Array*<br/>
Tableau unidimensionnel avec les valeurs de classement.

*_I*<br/>
Emplacement d’index dans un index unidimensionnel.

*_I0*<br/>
Longueur de la dimension la plus significative.

*_I1*<br/>
Longueur de la dimension suivante à la plus significative.

*_I2*<br/>
Longueur de la dimension la moins significative.

*_Other*<br/>
Objet d’index sur lequel est basé le nouvel objet d’index.

## <a name="operator--"></a><a name="operator--"></a> opérateur--

Décrémente chaque élément de l’objet index.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valeurs retournées

Pour l’opérateur préfixé, l’objet index (* this). Pour l’opérateur de suffixe, un nouvel objet d’index.

## <a name="operator"></a><a name="operator_mod_eq"></a> opérateur% =

Calcule le modulo (reste) de chaque élément de l’objet index lorsque cet élément est divisé par le nombre spécifié.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre par lequel diviser pour trouver le modulo.

## <a name="return-value"></a>Valeur renvoyée

Objet d’index.

## <a name="operator"></a><a name="operator_star_eq"></a> opérateur * =

Multiplie chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à multiplier.

## <a name="operator"></a><a name="operator_div_eq"></a> opérateur/=

Divise chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre par lequel diviser.

## <a name="operator"></a><a name="operator_at"></a> and\[\]

Retourne le composant de l’index à l’emplacement spécifié.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Entier compris entre 0 et le rang moins 1.

### <a name="return-value"></a>Valeur renvoyée

Élément situé à l’index spécifié.

### <a name="remarks"></a>Notes

L’exemple suivant affiche les valeurs de composant de l’index.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a> opérateur + +

Incrémente chaque élément de l’objet index.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur renvoyée

Pour l’opérateur préfixé, l’objet index (* this). Pour l’opérateur de suffixe, un nouvel objet d’index.

## <a name="operator"></a><a name="operator_add_eq"></a> opérateur + =

Ajoute le nombre spécifié à chaque élément de l’objet index.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Objet d’index.

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet d’index spécifié dans celui-ci.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet d’index à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Référence à cet objet d’index.

## <a name="operator-"></a><a name="operator_-_eq"></a> opérateur =

Soustrait le nombre spécifié de chaque élément de l’objet index.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à soustraire.

### <a name="return-value"></a>Valeur renvoyée

Objet d’index.

## <a name="rank"></a><a name="rank"></a> Moteurs

Obtient le rang de l’objet index.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
