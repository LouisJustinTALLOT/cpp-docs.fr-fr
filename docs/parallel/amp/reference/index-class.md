---
title: index, classe
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365154"
---
# <a name="index-class"></a>index, classe

Définit *un*vecteur d’index N-dimensionnel.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Le rang, ou le nombre de dimensions.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Index Constructeur](#index_ctor)|Initialise une nouvelle instance de la classe `index`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur--](#operator--)|Décrète chaque élément `index` de l’objet.|
|[l’opérateur %](#operator_mod_eq)|Calcule le modulus (reste) de `index` chaque élément de l’objet lorsque cet élément est divisé par un nombre.|
|[opérateur](#operator_star_eq)|Multiplie chaque élément `index` de l’objet par un nombre.|
|[opérateur/MD](#operator_div_eq)|Divise chaque élément `index` de l’objet par un nombre.|
|[indice::opérateur\[\]](#operator_at)|Retourne l’élément qui est à l’indice spécifié.|
|[opérateur](#operator_add_add)|Incréments chaque élément `index` de l’objet.|
|[opérateur](#operator_add_eq)|Ajoute le nombre spécifié à `index` chaque élément de l’objet.|
|[opérateur](#operator_eq)|Copie le contenu `index` de l’objet spécifié dans celui-ci.|
|[opérateur-MD](#operator_-_eq)|Soustrait le nombre spécifié de `index` chaque élément de l’objet.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[rang Constant](#rank)|Stocke le `index` rang de l’objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`index`

## <a name="remarks"></a>Notes

La `index` structure représente un vecteur *de* coordonnées des n’adenteurs qui spécifie une position unique dans *un*espace N-dimensionnel. Les valeurs du vecteur sont commandées de la plus importante à la moins significative. Vous pouvez récupérer les valeurs des composants à l’aide de [l’opérateur.](#operator_eq)

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="index-constructor"></a><a name="index_ctor"></a>Index Constructeur

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
Un tableau unidimensionnel avec les valeurs de rang.

*_I*<br/>
L’emplacement de l’indice dans un index unidimensionnel.

*_I0*<br/>
La longueur de la dimension la plus significative.

*_I1*<br/>
La longueur de la dimension la plus proche à la plus importante.

*_I2*<br/>
La longueur de la dimension la moins significative.

*_Other*<br/>
Un objet indiciel sur lequel le nouvel objet indiciel est basé.

## <a name="operator--"></a><a name="operator--"></a>opérateur--

Décroisse chaque élément de l’objet indiciel.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valeurs retournées

Pour l’opérateur de préfixe, l’objet de l’index (ce). Pour l’opérateur de suffixe, un nouvel objet index.

## <a name="operator"></a><a name="operator_mod_eq"></a>l’opérateur %

Calcule le modulus (reste) de chaque élément de l’objet index lorsque cet élément est divisé par le nombre spécifié.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le nombre à diviser pour trouver le modulus.

## <a name="return-value"></a>Valeur de retour

L’objet de l’index.

## <a name="operator"></a><a name="operator_star_eq"></a>opérateur

Multiplie chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le nombre à multiplier.

## <a name="operator"></a><a name="operator_div_eq"></a>opérateur/MD

Divise chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le nombre à diviser par.

## <a name="operator"></a><a name="operator_at"></a>Opérateur\[\]

Retourne la composante de l’index à l’emplacement spécifié.

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
Un intégrant de 0 à travers le rang moins 1.

### <a name="return-value"></a>Valeur de retour

L’élément qui est à l’index spécifié.

### <a name="remarks"></a>Notes

Cet exemple suivant affiche les valeurs des composants de l’indice.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>opérateur

Incréments chaque élément de l’objet index.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur de préfixe, l’objet de l’index (ce). Pour l’opérateur de suffixe, un nouvel objet index.

## <a name="operator"></a><a name="operator_add_eq"></a>opérateur

Ajoute le nombre spécifié à chaque élément de l’objet indexé.

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
Le numéro à ajouter.

### <a name="return-value"></a>Valeur de retour

L’objet de l’index.

## <a name="operator"></a><a name="operator_eq"></a>opérateur

Copie le contenu de l’objet index spécifié dans celui-ci.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
L’objet index à copier à partir.

### <a name="return-value"></a>Valeur de retour

Une référence à cet objet index.

## <a name="operator-"></a><a name="operator_-_eq"></a>opérateur-MD

Soustrait le nombre spécifié de chaque élément de l’objet indexé.

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
Le numéro à soustraire.

### <a name="return-value"></a>Valeur de retour

L’objet de l’index.

## <a name="rank"></a><a name="rank"></a>Rang

Obtient le rang de l’objet d’index.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
