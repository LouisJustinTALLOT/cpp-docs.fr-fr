---
title: extent, classe (C++ AMP)
ms.date: 11/04/2016
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
ms.openlocfilehash: 2236b1a1b72f307dae1efa0cfe197e222820c460
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270187"
---
# <a name="extent-class-c-amp"></a>extent, classe (C++ AMP)

Représente un vecteur de *N* entiers qui spécifient les limites d’un *N*-espace dimensionnel dont l’origine de 0. Les valeurs du vecteur sont triés du plus significatif au moins significatif.

### <a name="syntax"></a>Syntaxe

```
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Le rang de le `extent` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrence

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Extent, constructeur](#ctor)|Initialise une nouvelle instance de la classe `extent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[contains](#contains)|Vérifie que le texte spécifié `extent` objet a le rang spécifié.|
|[size](#size)|Retourne la taille totale linéaire de l’étendue (en unités d’éléments).|
|[tile](#tile)|Génère un `tiled_extent` objet avec les étendues de mosaïque donnée par les dimensions spécifiées.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator-](#operator_min)|Retourne un nouvel `extent` objet qui est créé en soustrayant le `index` éléments correspondants `extent` éléments.|
|[operator--](#operator_min_min)|Décrémente chaque élément de la `extent` objet.|
|[operator%=](#operator_mod_eq)|Calcule le modulo (reste) de chaque élément dans le `extent` de l’objet lorsque cet élément est divisé par un nombre.|
|[operator*=](#operator_star_eq)|Multiplie chaque élément de la `extent` objet par un nombre.|
|[operator/=](#operator_min_eq)|Divise chaque élément de la `extent` objet par un nombre.|
|[extent::operator\[\]](#operator_at)|Retourne l’élément qui est à l’index spécifié.|
|[operator+](#operator_add)|Retourne un nouvel `extent` objet qui est créé en ajoutant le correspondantes `index` et `extent` éléments.|
|[operator++](#operator_add_add)|Incrémente chaque élément de la `extent` objet.|
|[operator+=](#operator_add_eq)|Ajoute le nombre spécifié pour chaque élément de la `extent` objet.|
|[operator=](#operator_eq)|Copie le contenu d’un autre `extent` objet dans celui-ci.|
|[operator-=](#operator_min_eq)|Soustrait le nombre spécifié de chaque élément de la `extent` objet.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[rang (constante)](#rank)|Obtient le rang de le `extent` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`extent`

## <a name="contains"></a> contient

Indique si le texte spécifié [index](index-class.md) valeur est contenue dans l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Le `index` valeur à tester.

### <a name="return-value"></a>Valeur de retour

**true** si spécifié *index* valeur est contenue dans le `extent` objet ; sinon, **false**.

##  <a name="ctor"></a> étendue

Initialise une nouvelle instance de la classe « étendue ».

### <a name="syntax"></a>Syntaxe

```
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Array*<br/>
Un tableau de `_Rank` entiers qui est utilisé pour créer la nouvelle `extent` objet.

*_I*<br/>
La longueur de l’étendue.

*_I0*<br/>
La longueur de la dimension la plus significative.

*_I1*<br/>
La longueur de la dimension suivant-à-plus significatif.

*_I2*<br/>
La longueur de la dimension la moins significative.

*_Other*<br/>
Un `extent` objet sur lequel la nouvelle `extent` objet est basé.

## <a name="remarks"></a>Notes

Le constructeur sans paramètre initialise un `extent` objet ayant un rang de trois.

Si un tableau est utilisé pour construire un `extent` de l’objet, la longueur du tableau doit correspondre au rang de le `extent` objet.

##  <a name="operator_mod_eq"></a> operator%=

Calcule le modulo (reste) de chaque élément dans le « étendue » lorsque cet élément est divisé par un nombre.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à trouver le modulo de.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

##  <a name="operator_star_eq"></a> operator*=

Multiplie chaque élément dans l’objet « étendue » par le nombre spécifié.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à multiplier.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

## <a name="operator_add"></a> operator +

Retourne un nouvel `extent` objet créé en ajoutant le correspondantes `index` et `extent` éléments.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le `index` objet qui contient les éléments à ajouter.

### <a name="return-value"></a>Valeur de retour

Nouvel objet `extent` .

##  <a name="operator_add_add"></a> operator ++

Incrémente chaque élément de l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur de préfixe, le `extent` objet (`*this`). Pour l’opérateur de suffixe, un nouveau `extent` objet.

##  <a name="operator_add_eq"></a> operator+=

Ajoute le nombre spécifié pour chaque élément de l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le nombre, l’index ou étendue à ajouter.

### <a name="return-value"></a>Valeur de retour

Objet `extent` obtenu.

##  <a name="operator_min"></a> operator-

Crée un `extent` objet en soustrayant chaque élément spécifié `index` objet à partir de l’élément correspondant dans ce `extent` objet.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Le `index` objet qui contient les éléments à soustraire.

### <a name="return-value"></a>Valeur de retour

Nouvel objet `extent` .

##  <a name="operator_min_min"></a> operator--

Décrémente chaque élément dans l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Pour l’opérateur de préfixe, le `extent` objet (`*this`). Pour l’opérateur de suffixe, un nouveau `extent` objet.

##  <a name="operator_div_eq"></a> operator/=

Divise chaque élément dans l’objet « étendue » par le nombre spécifié.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à diviser par.

### <a name="return-value"></a>Valeur de retour

Objet `extent`.

##  <a name="operator_min_eq"></a> operator-=

Soustrait le nombre spécifié de chaque élément de l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Nombre à soustraire.

### <a name="return-value"></a>Valeur de retour

Objet `extent` obtenu.

##  <a name="operator_eq"></a> operator=

Copie le contenu d’un autre objet « étendue » dans celle-ci.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Le `extent` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `extent` objet.

##  <a name="operator_at"></a> Extent::operator \[\]

Retourne l’élément qui est à l’index spécifié.

### <a name="syntax"></a>Syntaxe

```
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Entier compris entre 0 et le rang moins 1.

### <a name="return-value"></a>Valeur de retour

L’élément qui est à l’index spécifié.

##  <a name="rank_constant"></a> rang

Stocke le rang de l’objet « étendue ».

### <a name="syntax"></a>Syntaxe

```
static const int rank = _Rank;
```

##  <a name="size"></a> Taille

Retourne la taille totale linéaire de la `extent` objet (en unités d’éléments).

### <a name="syntax"></a>Syntaxe

```
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a> vignette

Produit un objet tiled_extent avec les dimensions de mosaïque spécifiées.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Paramètres

*_Dim0*<br/>
Le composant le plus significatif de l’étendue en mosaïque.
*_Dim1*<br/>
Le composant suivant-à-plus significatif de l’étendue en mosaïque.
*_Dim2*<br/>
Composant le moins significatif de l’étendue en mosaïque.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
