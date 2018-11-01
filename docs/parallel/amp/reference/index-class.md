---
title: index, classe
ms.date: 11/04/2016
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 921d87de72c13e1971d9b40474bf3d91033c0580
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529309"
---
# <a name="index-class"></a>index, classe

Définit un *N*-index dimensionnel pographics-cpp-amp.md.

## <a name="syntax"></a>Syntaxe

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Le rang, ou le nombre de dimensions.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[index, constructeur](#ctor)|Initialise une nouvelle instance de la classe `index`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator--](#operator--)|Décrémente chaque élément de la `index` objet.|
|[operator(mod)=](#operator_mod_eq)|Calcule le modulo (reste) de chaque élément dans le `index` de l’objet lorsque cet élément est divisé par un nombre.|
|[operator*=](#operator_star_eq)|Multiplie chaque élément de la `index` objet par un nombre.|
|[operator/=](#operator_div_eq)|Divise chaque élément de la `index` objet par un nombre.|
|[index::operator\[\]](#operator_at)|Retourne l’élément qui est à l’index spécifié.|
|[operator++](#operator_add_add)|Incrémente chaque élément de la `index` objet.|
|[operator+=](#operator_add_eq)|Ajoute le nombre spécifié pour chaque élément de la `index` objet.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `index` objet dans celui-ci.|
|[operator-=](#operator_-_eq)|Soustrait le nombre spécifié de chaque élément de la `index` objet.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[rang (constante)](#rank)|Stocke le rang de le `index` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`index`

## <a name="remarks"></a>Notes

Le `index` structure représente un vecteur de coordonnées de *N* entiers qui spécifie une position unique dans une *N*-espace 3D. Les valeurs du vecteur sont triés du plus significatif au moins significatif. Vous pouvez récupérer les valeurs des composants à l’aide de [opérateur =](#operator_eq).

## <a name="requirements"></a>Configuration requise

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="index_ctor"></a> index, constructeur

Initialise une nouvelle instance de la classe d’index.

```
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

*_ARRAY*<br/>
Un tableau unidimensionnel avec les valeurs de classement.

*_I*<br/>
L’emplacement d’index dans un index unidimensionnel.

*_I0*<br/>
La longueur de la dimension la plus significative.

*_I1*<br/>
La longueur de la dimension suivant-à-plus significatif.

*_I2*<br/>
La longueur de la dimension la moins significative.

*_Autre*<br/>
Objet index sur lequel est basé le nouvel objet index.

## <a name="operator--"></a>  operator--

Décrémente chaque élément de l’objet index.
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valeurs de retour

Pour l’opérateur de préfixe, l’objet index (* cela). Pour l’opérateur de suffixe, un nouvel objet index.

## <a name="operator_mod_eq"></a>  operator(MOD) =

Calcule le modulo (reste) de chaque élément dans l’objet index lorsque cet élément est divisé par le nombre spécifié.

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à diviser par pour trouver le modulo.

## <a name="return-value"></a>Valeur de retour
L’objet index.

## <a name="operator_star_eq"></a>  operator*=

Multiplie chaque élément dans l’objet index par le nombre spécifié.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à multiplier.

## <a name="operator_div_eq"></a>  / =, opérateur

Divise chaque élément dans l’objet index par le nombre spécifié.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à diviser par.

## <a name="operator_at"></a>  operator\[\]

Retourne le composant de l’index à l’emplacement spécifié.

```
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

L’élément qui est à l’index spécifié.

### <a name="remarks"></a>Notes

L’exemple suivant affiche les valeurs de composant de l’index.
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator ++

Incrémente chaque élément de l’objet index.
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur de préfixe, l’objet index (* cela). Pour l’opérateur de suffixe, un nouvel objet index.

## <a name="operator_add_eq"></a>  opérateur +=

Ajoute le nombre spécifié pour chaque élément de l’objet index.
```
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

L’objet index.

## <a name="operator_eq"></a>  operator=

Copie le contenu de l’objet de l’index spécifié dans celui-ci.
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
L’objet index à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à cet objet index.

## <a name="operator_-_eq"></a>  operator-=

Soustrait le nombre spécifié de chaque élément de l’objet index.
```
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

L’objet index.

## <a name="rank"></a>  rang
  Obtient le rang de l’objet index.
```
static const int rank = _Rank;
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
