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
ms.openlocfilehash: 1a66e4d025a7592b78839dbe5f25f9103da41224
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535953"
---
# <a name="sampler-class"></a>sampler, classe

La classe d’échantillonnage regroupe les informations de configuration d’échantillonnage à utiliser pour l’échantillonnage de texture.

## <a name="syntax"></a>Syntaxe

```cpp
class sampler;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[échantillonneur, constructeur](#ctor)|Surchargé. Construit une instance d’échantillonnage.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Retourne le `address_mode` qui est associé à l’objet d’échantillonnage.|
|[get_border_color](#get_border_color)|Retourne la couleur de bordure qui est associé à l’objet d’échantillonnage.|
|[get_filter_mode](#get_filter_mode)|Retourne le `filter_mode` qui est associé à l’objet d’échantillonnage.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Surchargé. Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[address_mode](#address_mode)|Obtient le mode d’adresse de la `sampler` objet.|
|[border_color](#border_color)|Obtient la couleur de bordure de la `sampler` objet.|
|[filter_mode](#filter_mode)|Obtient le mode de filtre de le `sampler` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`sampler`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_graphics.h

**Namespace :** concurrency::graphics

##  <a name="ctor"></a> échantillonneur

Construit une instance de la [sampler, classe](sampler-class.md).

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
Mode de filtre à utiliser dans l’échantillonnage.

*_Address_mode*<br/>
Le mode d’adressage à utiliser dans l’échantillonnage pour toutes les dimensions.

*_Border_color*<br/>
La couleur de bordure à utiliser si le mode d’adresse est address_border. La valeur par défaut est `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Autre*<br/>
[5] constructeur de copie le `sampler` objet à copier dans le nouvel `sampler` instance.

[6] constructeur de déplacement le `sampler` déplacer dans le nouvel objet `sampler` instance.

##  <a name="address_mode"></a> address_mode

Obtient le mode d’adresse de la `sampler` objet.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

Obtient la couleur de bordure de la `sampler` objet.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode

Obtient le mode de filtre de le `sampler` objet.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

Retourne le mode de filtre qui est configuré pour ce `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Valeur de retour

Le mode d’adresse qui est configuré pour l’échantillonneur.

##  <a name="get_border_color"></a> get_border_color

Retourne la couleur de bordure qui est configurée pour ce `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Une valeur float_4 qui contient la couleur de bordure.

##  <a name="get_filter_mode"></a> get_filter_mode

Retourne le mode de filtre qui est configuré pour ce `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Le mode de filtre qui est configuré pour l’échantillonneur.

##  <a name="operator_eq"></a> opérateur =

Assigne la valeur d’un autre objet d’échantillonnage à un échantillonnage existant.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
[1] opérateur d’assignation de copie le `sampler` objet à copier dans cette `sampler`.

[2] opérateur d’assignation de déplacement le `sampler` objet à déplacer dans cette `sampler`.

### <a name="return-value"></a>Valeur de retour

Une référence à cette instance d’échantillonnage.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
