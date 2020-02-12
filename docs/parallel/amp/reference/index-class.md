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
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127801"
---
# <a name="index-class"></a>index, classe

Définit un vecteur d’index à *N*dimensions.

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

|Name|Description|
|----------|-----------------|
|[Constructeur d’index](#index_ctor)|Initialise une nouvelle instance de la classe `index`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator--](#operator--)|Décrémente chaque élément de l’objet `index`.|
|[operator%=](#operator_mod_eq)|Calcule le modulo (reste) de chaque élément de l’objet `index` lorsque cet élément est divisé par un nombre.|
|[operator*=](#operator_star_eq)|Multiplie chaque élément de l’objet `index` par un nombre.|
|[operator/=](#operator_div_eq)|Divise chaque élément de l’objet `index` par un nombre.|
|[index :: Operator\[\]](#operator_at)|Retourne l’élément qui se trouve à l’index spécifié.|
|[operator++](#operator_add_add)|Incrémente chaque élément de l’objet `index`.|
|[operator+=](#operator_add_eq)|Ajoute le nombre spécifié à chaque élément de l’objet `index`.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `index` spécifié dans celui-ci.|
|[operator-=](#operator_-_eq)|Soustrait le nombre spécifié de chaque élément de l’objet `index`.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Stocke le rang de l’objet `index`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`index`

## <a name="remarks"></a>Notes

La structure `index` représente un vecteur de coordonnées de *n* entiers qui spécifie une position unique dans un espace à *n*dimensions. Les valeurs du vecteur sont triées du plus significatif au moins significatif. Vous pouvez récupérer les valeurs des composants à l’aide de [Operator =](#operator_eq).

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="index_ctor"></a>Constructeur d’index

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

## <a name="operator--"></a>opérateur--

Décrémente chaque élément de l’objet index.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valeurs retournées

Pour l’opérateur préfixé, l’objet index (* this). Pour l’opérateur de suffixe, un nouvel objet d’index.

## <a name="operator_mod_eq"></a>opérateur% =

Calcule le modulo (reste) de chaque élément de l’objet index lorsque cet élément est divisé par le nombre spécifié.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre par lequel diviser pour trouver le modulo.

## <a name="return-value"></a>Valeur de retour

Objet d’index.

## <a name="operator_star_eq"></a>opérateur * =

Multiplie chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à multiplier.

## <a name="operator_div_eq"></a>opérateur/=

Divise chaque élément de l’objet index par le nombre spécifié.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre par lequel diviser.

## <a name="operator_at"></a>  operator\[\]

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

### <a name="return-value"></a>Valeur de retour

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

## <a name="operator_add_add"></a>opérateur + +

Incrémente chaque élément de l’objet index.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur préfixé, l’objet index (* this). Pour l’opérateur de suffixe, un nouvel objet d’index.

## <a name="operator_add_eq"></a>opérateur + =

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

### <a name="return-value"></a>Valeur de retour

Objet d’index.

## <a name="operator_eq"></a>  operator=

Copie le contenu de l’objet d’index spécifié dans celui-ci.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet d’index à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet d’index.

## <a name="operator_-_eq"></a>opérateur =

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

### <a name="return-value"></a>Valeur de retour

Objet d’index.

## <a name="rank"></a>Moteurs

Obtient le rang de l’objet index.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
