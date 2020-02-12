---
title: texture_view, classe
ms.date: 11/04/2016
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126344"
---
# <a name="texture_view-class"></a>texture_view, classe

Fournit un accès en lecture et un accès en écriture à une texture. `texture_view` ne peut être utilisé que pour lire les textures dont le type de valeur est `int`, `unsigned int`ou `float` qui ont la valeur par défaut 32 bits bpse. Pour lire d’autres formats de texture, utilisez `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type des éléments dans l’agrégat de texture.

*_Rank*<br/>
Rang du `texture_view`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`value_type`|Type des éléments dans les agrégats de texture.|
|`coordinates_type`|Type de la coordonnée utilisée pour spécifier un Texel dans le `texture_view`, c’est-à-dire un `short_vector` qui a le même rang que la texture associée qui a un type de valeur de `float`.|
|`gather_return_type`|Type de retour utilisé pour les opérations de collecte, c’est-à-dire un `short_vector` de rang 4 qui contient les quatre composants de couleur homogènes collectés à partir des quatre valeurs Texel échantillonnées.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur texture_view](#ctor)|Surchargé. Construit une instance de `texture_view`.|
|[Destructeur ~ texture_view](#ctor)|Détruit l’instance de `texture_view`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Surchargé. Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants alpha (w) des quatre texels échantillonnés.|
|[gather_blue](#gather_blue)|Surchargé. Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants bleus (z) des quatre texels échantillonnés.|
|[gather_green](#gather_green)|Surchargé. Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants verts (y) des quatre texels échantillonnés.|
|[gather_red](#gather_red)|Surchargé. Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants rouge (x) des quatre texels échantillonnés.|
|[get](#get)|Surchargé. Obtient la valeur de l’élément par index.|
|[sample](#sample)|Surchargé. Échantillonne la texture aux coordonnées et au niveau de détail spécifiés à l’aide de la configuration d’échantillonnage spécifiée.|
|[set](#set)|Définit la valeur d’un élément par index.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator()](#operator_call)|Surchargé. Obtient la valeur de l’élément par index.|
|[operator\[\]](#operator_at)|Surchargé. Obtient la valeur de l’élément par index.|
|[operator=](#operator_eq)|Surchargé. Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[value_type](#value_type)|Type de valeur des éléments de l' `texture_view`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency :: Graphics

## <a name="dtor"></a>~ texture_view

Détruit l’instance de `texture_view`.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

Construit une instance de `texture_view`.

```cpp
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
[1, 2] Constructeur `texture` sur lequel la `texture_view` accessible en écriture est créée.

[3,4] Constructeur `texture` sur lequel la `texture_view` non accessible en écriture est créée.

*_Other*<br/>
[5] constructeur de copie la `texture_view`accessible en écriture source.

[6, 7] Constructeur de copie la `texture_view`source non accessible en écriture.

*_Mipmap_level*<br/>
Niveau de mipmap spécifique sur le `texture` source auquel ce `texture_view` accessible en écriture est lié. La valeur par défaut est 0, qui représente le niveau MIP le plus élevé (le plus détaillé).

*_Most_detailed_mip*<br/>
Niveau MIP de niveau supérieur (le plus détaillé) pour la vue, relatif à l’objet `texture_view` spécifié.

*_Mip_levels*<br/>
Nombre de niveaux de mipmap accessibles via l' `texture_view`.

## <a name="gather_red"></a>gather_red

Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants rouge (x) des quatre texels échantillonnés.

```cpp
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Address_mode*<br/>
Mode d’adresse à utiliser pour échantillonner le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.

*_Sampler*<br/>
Configuration de l’échantillonneur à utiliser pour échantillonner le `texture_view`.

*_Coord*<br/>
Coordonnées à partir desquelles l’exemple doit être extrait. Les valeurs de coordonnées fractionnaires sont utilisées pour interpoler entre des texels d’échantillon.

### <a name="return-value"></a>Valeur de retour

Vecteur Short de rang 4 contenant le composant rouge (x) des 4 valeurs Texel échantillonnées.

## <a name="gather_green"></a>gather_green

Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants verts (y) des quatre texels échantillonnés.

```cpp
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Address_mode*<br/>
Mode d’adresse à utiliser pour échantillonner le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.

*_Sampler*<br/>
Configuration de l’échantillonneur à utiliser pour échantillonner le `texture_view`.

*_Coord*<br/>
Coordonnées à partir desquelles l’exemple doit être extrait. Les valeurs de coordonnées fractionnaires sont utilisées pour interpoler entre des texels d’échantillon.

### <a name="return-value"></a>Valeur de retour

Vecteur Short de rang 4 contenant le composant vert (y) des 4 valeurs Texel échantillonnées.

## <a name="gather_blue"></a>gather_blue

Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants bleus (z) des quatre texels échantillonnés.

```cpp
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Address_mode*<br/>
Mode d’adresse à utiliser pour échantillonner le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.

*_Sampler*<br/>
Configuration de l’échantillonneur à utiliser pour échantillonner le `texture_view`.

*_Coord*<br/>
Coordonnées à partir desquelles l’exemple doit être extrait. Les valeurs de coordonnées fractionnaires sont utilisées pour interpoler entre des texels d’échantillon.

### <a name="return-value"></a>Valeur de retour

Vecteur Short de rang 4 contenant le composant rouge (x) des 4 valeurs Texel échantillonnées.

## <a name="gather_alpha"></a>gather_alpha

Échantillonne la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifiée et retourne les composants alpha (w) des quatre texels échantillonnés.

```cpp
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Address_mode*<br/>
Mode d’adresse à utiliser pour échantillonner le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.

*_Sampler*<br/>
Configuration de l’échantillonneur à utiliser pour échantillonner le `texture_view`.

*_Coord*<br/>
Coordonnées à partir desquelles l’exemple doit être extrait. Les valeurs de coordonnées fractionnaires sont utilisées pour interpoler entre des texels d’échantillon.

### <a name="return-value"></a>Valeur de retour

Vecteur Short de rang 4 contenant le composant alpha (w) des 4 valeurs Texel échantillonnées.

## <a name="get"></a>Télécharger

Obtient la valeur de l’élément à l’index spécifié.

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l’élément à récupérer, éventuellement à plusieurs dimensions.

*_Mip_level*<br/>
Niveau de mipmap à partir duquel la valeur doit être obtenue. La valeur par défaut 0 représente le niveau de mipmap le plus détaillé.

### <a name="return-value"></a>Valeur de retour

Valeur de l'élément.

## <a name="operator_eq"></a>opérateur =

Assigne une vue de la même texture que la `texture_view` spécifiée à cette `texture_view` instance.

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
[1, 2] Constructeur de copie objet de `texture_view` accessible en écriture.

[3] constructeur de copie un objet de `texture_view` non accessible en écriture.

### <a name="return-value"></a>Valeur de retour

Référence à cette instance de `texture_view`.

## <a name="operator_at"></a>[], opérateur

Retourne la valeur de l’élément par index.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index, éventuellement multidimensionnel.

*_I0*<br/>
Index unidimensionnel.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément indexée par `_Index`.

## <a name="operator_call"></a>, opérateur ()

Retourne la valeur de l’élément par index.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index, éventuellement multidimensionnel.

*_I0*<br/>
Composant le plus significatif de l’index.

*_I1*<br/>
Composant suivant le plus significatif de l’index.

*_I2*<br/>
Composant le moins significatif de l’index.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément indexée par `_Index`.

## <a name="sample"></a>exemple

Échantillonne la texture aux coordonnées et au niveau de détail spécifiés à l’aide de la configuration d’échantillonnage spécifiée.

```cpp
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Filter_mode*<br/>
Mode de filtre à utiliser pour échantillonner le texture_view. Le mode de filtrage est le même pour les filtres de minimisation, de maximisation et de mipmap.

*_Address_mode*<br/>
Mode d’adresse à utiliser pour échantillonner le texture_view. Le mode d’adresse est le même pour toutes les dimensions.

*_Sampler*<br/>
Configuration de l’échantillonneur à utiliser pour échantillonner le texture_view.

*_Coord*<br/>
Coordonnées à partir desquelles l’exemple doit être extrait. Les valeurs de coordonnées fractionnaires sont utilisées pour interpoler entre les valeurs de Texel.

*_Level_of_detail*<br/>
La valeur spécifie le niveau de mipmap à partir duquel échantillonner. Les valeurs fractionnaires sont utilisées pour interpoler entre deux niveaux de mipmap. Le niveau de détail par défaut est 0, qui représente le niveau MIP le plus détaillé.

### <a name="return-value"></a>Valeur de retour

Valeur de l’échantillon interpolé.

## <a name="set"></a>définie

Affecte la valeur spécifiée à l’élément à l’index spécifié.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l’élément à définir, éventuellement à plusieurs dimensions.

*value*<br/>
Valeur avec laquelle définir l’élément.

## <a name="value_type"></a>value_type

Type de valeur des éléments de l’texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
