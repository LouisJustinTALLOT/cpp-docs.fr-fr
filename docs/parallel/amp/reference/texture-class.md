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
ms.openlocfilehash: f7a38c84c5def629c7a42b2c05bf1ed04441593b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127775"
---
# <a name="texture-class"></a>texture, classe

Une texture est un agrégat de données sur un `accelerator_view` dans le domaine de l’étendue. Il s’agit d’une collection de variables, une pour chaque élément dans un domaine d’étendue. Chaque variable contient une valeur correspondant au C++ type primitif (`unsigned int`, `int`, `float`, `double`), un type scalaire (`norm`ou `unorm`) ou un type Vector Short.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename value_type,  int _Rank>
class texture;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type des éléments de la texture.

*_Rank*<br/>
Rang de la texture.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`scalar_type`|Types scalaires.|
|`value_type`|Types valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur de texture](#ctor)|Initialise une nouvelle instance de la classe `texture`.|
|[~ texture, destructeur](#ctor)|Détruit l’objet `texture`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[copy_to](#copy_to)|Copie l’objet `texture` vers la destination, en procédant à une copie complète.|
|[data](#data)|Retourne un pointeur UC vers les données brutes de cette texture.|
|[get](#get)|Retourne la valeur de l’élément à l’index spécifié.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Retourne le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut pour la copie de cette texture.|
|[get_depth_pitch](#get_depth_pitch)|Retourne le nombre d’octets entre chaque secteur de profondeur dans une texture intermédiaire 3D sur l’UC.|
|[get_row_pitch](#get_row_pitch)|Retourne le nombre d’octets entre chaque ligne dans une texture intermédiaire 2D ou 3D sur l’UC.|
|[set](#set)|Définit la valeur de l’élément à l’index spécifié.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator()](#operator_call)|Retourne la valeur de l’élément qui est spécifiée par les paramètres.|
|[operator\[\]](#operator_at)|Retourne l’élément qui se trouve à l’index spécifié.|
|[operator=](#operator_eq)|Copie l’objet [texture](texture-class.md) spécifié dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Obtient le rang de l’objet `texture`.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Obtient le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut pour la copie de cette texture.|
|[depth_pitch](#depth_pitch)|Obtient le nombre d’octets entre chaque secteur de profondeur dans une texture intermédiaire 3D sur l’UC.|
|[row_pitch](#row_pitch)|Obtient le nombre d’octets entre chaque ligne dans une texture intermédiaire 2D ou 3D sur l’UC.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Texture_base`

`texture`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency :: Graphics

## <a name="dtor"></a>~ texture

Détruit l’objet `texture`.

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Obtient le [accelerator_view](accelerator-view-class.md) qui est la cible par défaut pour la copie de cette texture.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Copie l’objet `texture` vers la destination, en procédant à une copie complète.

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Objet cible de la copie.

*_Rank*<br/>
Rang de la texture.

*value_type*<br/>
Type des éléments de la texture.

## <a name="data"></a>métadonnée

Retourne un pointeur UC vers les données brutes de cette texture.

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers les données brutes de la texture.

## <a name="depth_pitch"></a>depth_pitch

Obtient le nombre d’octets entre chaque secteur de profondeur dans une texture intermédiaire 3D sur l’UC.

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a>Télécharger

Retourne la valeur de l’élément à l’index spécifié.

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l'élément.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément à l’index spécifié.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Retourne le accelerator_view qui est la cible par défaut pour la copie de cette texture.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

[Accelerator_view](accelerator-view-class.md) qui est la cible par défaut pour la copie de cette texture.

## <a name="get_depth_pitch"></a>get_depth_pitch

Retourne le nombre d’octets entre chaque secteur de profondeur dans une texture intermédiaire 3D sur l’UC.

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Nombre d’octets entre chaque secteur de profondeur dans une texture intermédiaire 3D sur l’UC.

## <a name="get_row_pitch"></a>get_row_pitch

Retourne le nombre d’octets entre chaque ligne dans une texture intermédiaire bidimensionnelle, ou entre chaque ligne d’un secteur de profondeur dans une texture intermédiaire à trois dimensions.

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

Nombre d’octets entre chaque ligne dans une texture intermédiaire bidimensionnelle, ou entre chaque ligne d’un secteur de profondeur dans une texture intermédiaire à trois dimensions.

## <a name="operator_call"></a>, opérateur ()

Retourne la valeur de l’élément qui est spécifiée par les paramètres.

```cpp
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
Composant le plus significatif de l’index.

*_I1*<br/>
Composant suivant le plus significatif de l’index.

*_I2*<br/>
Composant le moins significatif de l’index.

*_Rank*<br/>
Rang de l’index.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément qui est spécifiée par les paramètres.

## <a name="operator_at"></a>[], opérateur

Retourne l’élément qui se trouve à l’index spécifié.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

*_I0*<br/>
Index.

### <a name="return-value"></a>Valeur de retour

Élément qui se trouve à l’index spécifié.

## <a name="operator_eq"></a>opérateur =

Copie l’objet [texture](texture-class.md) spécifié dans celui-ci.

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `texture` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `texture`.

## <a name="rank"></a>moteurs

Obtient le rang de l’objet `texture`.

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a>row_pitch

Obtient le nombre d’octets entre chaque ligne dans une texture intermédiaire 2D ou 3D sur l’UC.

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a>définie

Définit la valeur de l’élément à l’index spécifié.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l'élément.

*_Rank*<br/>
Rang de l’index.

*value*<br/>
Nouvelle valeur de l’élément.

## <a name="ctor"></a>motif

Initialise une nouvelle instance de la classe `texture`.

```cpp
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
[Accelerator_view](accelerator-view-class.md) qui spécifie l’emplacement de la texture.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) qui spécifie l’emplacement de la texture.

*_Associated_av*<br/>
Accelerator_view qui spécifie la cible préférée pour les copies vers ou à partir de cette texture.

*_Bits_per_scalar_element*<br/>
Nombre de bits par élément scalaire dans le type scalaire sous-jacent de la texture. En général, les valeurs prises en charge sont 8, 16, 32 et 64. Si la valeur 0 est spécifiée, le nombre de bits est le même que le scalar_type sous-jacent. 64 est uniquement valide pour les textures de type double.

*_Ext*<br/>
L’étendue de chaque dimension de la texture.

*_E0*<br/>
Composant le plus significatif de la texture.

*_E1*<br/>
Composant suivant le plus significatif de la texture.

*_E2*<br/>
Composant le moins significatif de l’étendue de la texture.

*_Input_iterator*<br/>
Type de l'itérateur d'entrée.

*_Mipmap_levels*<br/>
Nombre de niveaux de mipmap dans la texture sous-jacente. Si la valeur 0 est spécifiée, la texture affiche la plage complète des niveaux de mipmap jusqu’à la plus petite taille possible pour l’étendue spécifiée.

*_Rank*<br/>
Rang de l’étendue.

*_Source*<br/>
Pointeur vers une mémoire tampon d’hôte.

*_Src*<br/>
À la texture à copier.

*_Src_byte_size*<br/>
Nombre d’octets dans la mémoire tampon source.

*_Src_first*<br/>
Itérateur de début dans le conteneur source.

*_Src_last*<br/>
Itérateur de fin dans le conteneur source.

*_Other*<br/>
Autre source de données.

*_Rank*<br/>
Rang de la section.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
