---
title: sampler, classe
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 8f47bf6e9b88dba1e94e9e2ed2b93c8d2d3f9b8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126349"
---
# <a name="sampler-class"></a>sampler, classe

La classe d’échantillonneur agrège les informations de configuration d’échantillonnage à utiliser pour l’échantillonnage de texture.

## <a name="syntax"></a>Syntaxe

```cpp
class sampler;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[sampler, constructeur](#ctor)|Surchargé. Construit une instance de l’échantillonneur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Retourne le `address_mode` associé à l’objet d’échantillonnage.|
|[get_border_color](#get_border_color)|Retourne la couleur de bordure associée à l’objet d’échantillonnage.|
|[get_filter_mode](#get_filter_mode)|Retourne le `filter_mode` associé à l’objet d’échantillonnage.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Surchargé. Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[address_mode](#address_mode)|Obtient le mode d’adresse de l’objet `sampler`.|
|[border_color](#border_color)|Obtient la couleur de bordure de l’objet `sampler`.|
|[filter_mode](#filter_mode)|Obtient le mode de filtre de l’objet `sampler`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`sampler`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency :: Graphics

## <a name="ctor"></a>échantillonneur

Construit une instance de la [classe d’échantillonnage](sampler-class.md).

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Paramètres

*_Filter_mode*<br/>
Mode de filtre à utiliser pour l’échantillonnage.

*_Address_mode*<br/>
Mode d’adressage à utiliser pour l’échantillonnage pour toutes les dimensions.

*_Border_color*<br/>
Couleur de la bordure à utiliser si le mode d’adresse est address_border. La valeur par défaut est `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Other*<br/>
[5] constructeur de copie l’objet `sampler` à copier dans la nouvelle instance `sampler`.

[6] Déplacez le constructeur de l’objet `sampler` pour le déplacer dans la nouvelle instance `sampler`.

## <a name="address_mode"></a>address_mode

Obtient le mode d’adresse de l’objet `sampler`.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a>border_color

Obtient la couleur de bordure de l’objet `sampler`.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a>filter_mode

Obtient le mode de filtre de l’objet `sampler`.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a>get_address_mode

Retourne le mode de filtre configuré pour ce `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Valeur de retour

Mode d’adresse configuré pour l’échantillonneur.

## <a name="get_border_color"></a>get_border_color

Retourne la couleur de bordure configurée pour ce `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Float_4 qui contient la couleur de la bordure.

## <a name="get_filter_mode"></a>get_filter_mode

Retourne le mode de filtre configuré pour ce `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Mode de filtre configuré pour l’échantillonneur.

## <a name="operator_eq"></a>opérateur =

Assigne la valeur d’un autre objet échantillonneur à un échantillonneur existant.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
[1] copier l’opérateur d’assignation l’objet `sampler` à copier dans ce `sampler`.

[2] déplacer l’opérateur d’assignation l’objet `sampler` à déplacer dans ce `sampler`.

### <a name="return-value"></a>Valeur de retour

Référence à cette instance de l’échantillonneur.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
