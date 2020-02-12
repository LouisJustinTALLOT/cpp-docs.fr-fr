---
title: extent, classe (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126719"
---
# <a name="extent-class-c-amp"></a>extent, classe (C++ AMP)

Représente un vecteur de *n* valeurs entières qui spécifient les limites d’un espace *n*-dimensionnel dont l’origine est 0. Les valeurs du vecteur sont triées du plus significatif au moins significatif.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang de l’objet `extent`.

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[extension, constructeur](#ctor)|Initialise une nouvelle instance de la classe `extent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[contains](#contains)|Vérifie que l’objet `extent` spécifié a le rang spécifié.|
|[size](#size)|Retourne la taille linéaire totale de l’étendue (en unités d’éléments).|
|[disposé](#tile)|Produit un objet `tiled_extent` avec les étendues de mosaïques fournies par les dimensions spécifiées.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator-](#operator_min)|Retourne un nouvel objet `extent` qui est créé en soustrayant les éléments `index` des éléments `extent` correspondants.|
|[operator--](#operator_min_min)|Décrémente chaque élément de l’objet `extent`.|
|[operator%=](#operator_mod_eq)|Calcule le modulo (reste) de chaque élément de l’objet `extent` lorsque cet élément est divisé par un nombre.|
|[operator*=](#operator_star_eq)|Multiplie chaque élément de l’objet `extent` par un nombre.|
|[operator/=](#operator_min_eq)|Divise chaque élément de l’objet `extent` par un nombre.|
|[extent :: Operator\[\]](#operator_at)|Retourne l’élément qui se trouve à l’index spécifié.|
|[operator+](#operator_add)|Retourne un nouvel objet `extent` qui est créé en ajoutant les éléments `index` et `extent` correspondants.|
|[operator++](#operator_add_add)|Incrémente chaque élément de l’objet `extent`.|
|[operator+=](#operator_add_eq)|Ajoute le nombre spécifié à chaque élément de l’objet `extent`.|
|[operator=](#operator_eq)|Copie le contenu d’un autre objet `extent` dans celui-ci.|
|[operator-=](#operator_min_eq)|Soustrait le nombre spécifié de chaque élément de l’objet `extent`.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Rank, constante](#rank_constant)|Obtient le rang de l’objet `extent`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`extent`

## <a name="contains"></a>comprend

Indique si la valeur d' [index](index-class.md) spécifiée est contenue dans l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Valeur `index` à tester.

### <a name="return-value"></a>Valeur de retour

**true** si la valeur d' *index* spécifiée est contenue dans l’objet `extent` ; Sinon, **false**.

## <a name="ctor"></a>étendue

Initialise une nouvelle instance de la classe « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Array*<br/>
Tableau d’entiers `_Rank` utilisé pour créer le nouvel objet `extent`.

*_I*<br/>
Longueur de l’étendue.

*_I0*<br/>
Longueur de la dimension la plus significative.

*_I1*<br/>
Longueur de la dimension suivante à la plus significative.

*_I2*<br/>
Longueur de la dimension la moins significative.

*_Other*<br/>
Objet `extent` sur lequel est basé le nouvel objet `extent`.

## <a name="remarks"></a>Notes

Le constructeur par défaut initialise un objet `extent` dont le rang est égal à trois.

Si un tableau est utilisé pour construire un objet `extent`, la longueur du tableau doit correspondre au rang de l’objet `extent`.

## <a name="operator_mod_eq"></a>opérateur% =

Calcule le modulo (reste) de chaque élément dans l’étendue lorsque cet élément est divisé par un nombre.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre dont le modulo doit être trouvé.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

## <a name="operator_star_eq"></a>opérateur * =

Multiplie chaque élément de l’objet « extent » par le nombre spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à multiplier.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

## <a name="operator_add"></a>opérateur +

Retourne un nouvel objet `extent` créé en ajoutant les éléments `index` et `extent` correspondants.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Objet `index` qui contient les éléments à ajouter.

### <a name="return-value"></a>Valeur de retour

Nouvel objet `extent`.

## <a name="operator_add_add"></a>opérateur + +

Incrémente chaque élément de l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur préfixé, l’objet `extent` (`*this`). Pour l’opérateur de suffixe, nouvel objet `extent`.

## <a name="operator_add_eq"></a>opérateur + =

Ajoute le nombre spécifié à chaque élément de l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre, index ou étendue à ajouter.

### <a name="return-value"></a>Valeur de retour

Objet `extent` obtenu.

## <a name="operator_min"></a>and

Crée un objet `extent` en soustrayant chaque élément de l’objet `index` spécifié de l’élément correspondant dans cet objet `extent`.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Objet `index` qui contient les éléments à soustraire.

### <a name="return-value"></a>Valeur de retour

Nouvel objet `extent`.

## <a name="operator_min_min"></a>opérateur--

Décrémente chaque élément de l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur préfixé, l’objet `extent` (`*this`). Pour l’opérateur de suffixe, nouvel objet `extent`.

## <a name="operator_div_eq"></a>opérateur/=

Divise chaque élément de l’objet « extent » par le nombre spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre par lequel diviser.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

## <a name="operator_min_eq"></a>opérateur =

Soustrait le nombre spécifié de chaque élément de l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à soustraire.

### <a name="return-value"></a>Valeur de retour

Objet `extent` obtenu.

## <a name="operator_eq"></a>opérateur =

Copie le contenu d’un autre objet « extension » dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `extent` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `extent`.

## <a name="operator_at"></a>extent :: Operator \[\]

Retourne l’élément qui se trouve à l’index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Entier compris entre 0 et le rang moins 1.

### <a name="return-value"></a>Valeur de retour

Élément situé à l’index spécifié.

## <a name="rank_constant"></a>moteurs

Stocke le rang de l’objet « extent ».

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>corps

Retourne la taille linéaire totale de l’objet `extent` (en unités d’éléments).

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>disposé

Produit un objet tiled_extent avec les dimensions de mosaïque spécifiées.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Paramètres

*_Dim0*<br/>
Composant le plus significatif de l’étendue en mosaïque.
*_Dim1*<br/>
Composant suivant le plus significatif de l’étendue en mosaïque.
*_Dim2*<br/>
Composant le moins significatif de l’étendue en mosaïque.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
