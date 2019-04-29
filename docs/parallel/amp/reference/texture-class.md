---
title: texture, classe
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: cfcb65fa23fe4593e7dcf11da3b5da4b1785ce71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351532"
---
# <a name="texture-class"></a>texture, classe

Une texture est un agrégat de données sur un `accelerator_view` dans le domaine de l’étendue. C’est un ensemble de variables, une pour chaque élément dans un domaine d’étendue. Chaque variable contient une valeur correspondant au type primitif C++ ( `unsigned int`, `int`, `float`, `double`), un type scalaire ( `norm`, ou `unorm`), ou un type vectoriel court.

## <a name="syntax"></a>Syntaxe

```
template <typename value_type,  int _Rank>
class texture;
```

#### <a name="parameters"></a>Paramètres

*value_type*<br/>
Le type des éléments de la texture.

*_Rank*<br/>
Le rang de la texture.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`scalar_type`|Types scalaires.|
|`value_type`|Les types de valeurs.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[texture, constructeur](#ctor)|Initialise une nouvelle instance de la classe `texture`.|
|[~ texture, destructeur](#ctor)|Détruit le `texture` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[copy_to](#copy_to)|Copie le `texture` objet vers la destination, en faisant une copie complète.|
|[data](#data)|Retourne un pointeur CPU vers les données brutes de cette texture.|
|[get](#get)|Retourne la valeur de l’élément à l’index spécifié.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Retourne le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut cette texture à copier vers.|
|[get_depth_pitch](#get_depth_pitch)|Retourne le nombre d’octets entre chaque secteur de profondeur dans une texture 3D intermédiaire de l’UC.|
|[get_row_pitch](#get_row_pitch)|Retourne le nombre d’octets entre chaque ligne d’un 2D ou d’une texture 3D intermédiaire de l’UC.|
|[set](#set)|Définit la valeur de l’élément à l’index spécifié.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator()](#operator_call)|Retourne la valeur de l’élément qui est spécifiée par les paramètres.|
|[operator\[\]](#operator_at)|Retourne l’élément qui est à l’index spécifié.|
|[operator=](#operator_eq)|Copie le texte spécifié [texture](texture-class.md) objet à celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[rang (constante)](#rank)|Obtient le rang de le `texture` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Obtient le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut cette texture à copier vers.|
|[depth_pitch](#depth_pitch)|Obtient le nombre d’octets entre chaque secteur de profondeur dans une texture 3D intermédiaire de l’UC.|
|[row_pitch](#row_pitch)|Obtient le nombre d’octets entre chaque ligne dans un 2D ou 3D un intermédiaire texture sur l’UC.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Texture_base`

`texture`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_graphics.h

**Espace de noms :** Concurrency::graphics

##  <a name="dtor"></a> ~texture

Détruit le `texture` objet.

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

Obtient le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut cette texture à copier vers.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

Copie le `texture` objet vers la destination, en faisant une copie complète.

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’objet dans lequel copier.

*_Rank*<br/>
Le rang de la texture.

*value_type*<br/>
Le type des éléments de la texture.

##  <a name="data"></a> Données

Retourne un pointeur CPU vers les données brutes de cette texture.

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers les données brutes de la texture.

##  <a name="depth_pitch"></a> depth_pitch

Obtient le nombre d’octets entre chaque secteur de profondeur dans une texture 3D intermédiaire de l’UC.

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> Télécharger

Retourne la valeur de l’élément à l’index spécifié.

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
L’index de l’élément.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément à l’index spécifié.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

Retourne l’accelerator_view qui est la cible par défaut pour cette texture à copier vers.

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut cette texture à copier vers.

##  <a name="get_depth_pitch"></a> get_depth_pitch

Retourne le nombre d’octets entre chaque secteur de profondeur dans une texture 3D intermédiaire de l’UC.

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets entre chaque secteur de profondeur dans une texture 3D intermédiaire de l’UC.

##  <a name="get_row_pitch"></a> get_row_pitch

Retourne le nombre d’octets entre chaque ligne dans une texture intermédiaire 2D, ou entre chaque ligne d’un secteur de profondeur dans 3-texture intermédiaire tridimensionnelle.

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets entre chaque ligne dans une texture intermédiaire 2D, ou entre chaque ligne d’un secteur de profondeur dans 3-texture intermédiaire tridimensionnelle.

##  <a name="operator_call"></a> operator()

Retourne la valeur de l’élément qui est spécifiée par les paramètres.

```
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

*_I0*<br/>
Le composant plus significatif de l’index.

*_I1*<br/>
Le composant suivant-à-plus significatif de l’index.

*_I2*<br/>
Le composant moins significatif de l’index.

*_Rank*<br/>
Le rang de l’index.

### <a name="return-value"></a>Valeur de retour

La valeur de l’élément qui est spécifiée par les paramètres.

##  <a name="operator_at"></a> operator]

Retourne l’élément qui est à l’index spécifié.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

*_I0*<br/>
Index.

### <a name="return-value"></a>Valeur de retour

L’élément qui est à l’index spécifié.

##  <a name="operator_eq"></a> operator=

Copie le texte spécifié [texture](texture-class.md) objet à celui-ci.

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Le `texture` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `texture` objet.

##  <a name="rank"></a> rang

Obtient le rang de le `texture` objet.

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

Obtient le nombre d’octets entre chaque ligne dans un 2D ou 3D un intermédiaire texture sur l’UC.

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> Ensemble

Définit la valeur de l’élément à l’index spécifié.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
L’index de l’élément.

*_Rank*<br/>
Le rang de l’index.

*value*<br/>
Nouvelle valeur de l’élément.

##  <a name="ctor"></a> texture

Initialise une nouvelle instance de la classe `texture`.

```
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>Paramètres

*_Acc_view*<br/>
Le [accelerator_view](accelerator-view-class.md) qui spécifie l’emplacement de la texture.

*_Av*<br/>
Le [accelerator_view](accelerator-view-class.md) qui spécifie l’emplacement de la texture.

*_Associated_av*<br/>
Un accelerator_view qui spécifie la cible par défaut copie vers ou à partir de cette texture.

*_Bits_per_scalar_element*<br/>
Le nombre de bits pour chaque élément scalaire dans le type scalaire sous-jacent de la texture. En règle générale, la valeur prise en charge sont 8, 16, 32 et 64. Si 0 est spécifié, le nombre de bits est le même scalar_type sous-jacent. 64 est uniquement valide pour les textures à double base.

*_Ext*<br/>
Objet extent dans chaque dimension de la texture.

*_E0*<br/>
Le composant le plus significatif de la texture.

*_E1*<br/>
Le composant suivant-à-plus significatif de la texture.

*_E2*<br/>
Composant le moins significatif de l’étendue de la texture.

*_Input_iterator*<br/>
Le type de l’itérateur d’entrée.

*_Mipmap_levels*<br/>
Le nombre de niveaux de mipmap dans la texture sous-jacente. Si 0 est spécifié, la texture dispose de la gamme complète de niveaux de mipmap jusqu'à la plus petite taille possible pour l’étendue spécifiée.

*_Rank*<br/>
Le rang de l’étendue.

*_Source*<br/>
Pointeur vers une mémoire tampon hôte.

*_Src*<br/>
Pour texturer pour copier.

*_Src_byte_size*<br/>
Le nombre d’octets dans la mémoire tampon source.

*_Src_first*<br/>
Un itérateur de départ dans le conteneur source.

*_Src_last*<br/>
Un itérateur de fin dans le conteneur source.

*_Other*<br/>
Autre source de données.

*_Rank*<br/>
Le rang de la section.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
