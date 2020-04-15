---
title: Concurrency::graphics::direct3d, fonctions de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 330c1aa94b1d122901fc23576686032400249d31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376388"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d, fonctions de l’espace de noms

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4 msad4](#msad4)|

## <a name="get_sampler"></a><a name="get_sampler"></a>get_sampler

Obtenez l’interface d’état de l’échantillonneur D3D sur la vue d’accélérateur donnée qui représente l’objet échantillonneur spécifié.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Une vue d’accélérateur D3D sur laquelle l’état d’échantillonneur D3D doit être créé.

*_Sampler*<br/>
Un objet sampler pour lequel l’interface d’état d’échantillonneur D3D sous-jacente est créée.

### <a name="return-value"></a>Valeur de retour

Le pointeur d’interface IUnknown correspondant à l’état d’échantillonneur D3D qui représente l’échantillonneur donné.

## <a name="get_texture"></a><a name="get_texture"></a>get_texture

Obtient l’interface de texture Direct3D sous-jacente à l’objet [de texture](texture-class.md) spécifié.

```cpp
template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Le type d’élément de la texture.

*_Rank*<br/>
Le rang de la texture.

*_Texture*<br/>
Une vue de texture ou de texture associée au accelerator_view pour lequel l’interface de texture directe sous-jacente est retournée.

### <a name="return-value"></a>Valeur de retour

Le pointeur d’interface IUnknown correspondant à la texture Direct3D sous-jacente à la texture.

## <a name="make_sampler"></a><a name="make_sampler"></a>make_sampler

Créez un échantillonneur à partir d’un pointeur d’interface d’état d’échantillonneur D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_D3D_sampler*<br/>
IUnknown interface pointeur de l’état échantillonneur D3D pour créer l’échantillonneur à partir.

### <a name="return-value"></a>Valeur de retour

Un échantillonneur représente l’état d’échantillonneur D3D fourni.

## <a name="make_texture"></a><a name="make_texture"></a>make_texture

Crée un objet [de texture](texture-class.md) en utilisant les paramètres spécifiés.

```cpp
template<
    typename value_type,
    int _Rank
>
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,
    _In_ IUnknown* _D3D_texture,
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Le type d’éléments dans la texture.

*_Rank*<br/>
Le rang de la texture.

*_Av*<br/>
Une vue d’accélérateur D3D sur laquelle la texture doit être créée.

*_D3D_texture*<br/>
IUnknown interface pointeur de la texture D3D pour créer la texture à partir.

*_View_format*<br/>
Le format DXGI à utiliser pour les vues créées à partir de cette texture. Passer DXGI_FORMAT_UNKNOWN (par défaut) pour tirer le format du format sous-jacent de _D3D_texture et le value_type de ce modèle. Le format fourni doit être compatible avec le format sous-jacent de _D3D_texture.

### <a name="return-value"></a>Valeur de retour

Une texture utilisant la texture D3D fournie.

## <a name="msad4"></a><a name="msad4"></a>msad4 msad4

Compare une valeur de référence de 4-byte et une valeur source de 8 byte et accumule un vecteur de 4 sommes. Chaque somme correspond à la somme masquée des différences absolues de différents alignements d’byte entre la valeur de référence et la valeur source.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Reference*<br/>
La gamme de référence de 4 octets en une seule valeur uint

*_Source*<br/>
La gamme source de 8 octets dans un vecteur de deux valeurs uint.

*_Accum*<br/>
Un vecteur de 4 valeurs à ajouter à la somme masquée des différences absolues des différents alignements d’byte entre la valeur de référence et la valeur source.

### <a name="return-value"></a>Valeur de retour

Retourne un vecteur de 4 sommes. Chaque somme correspond à la somme masquée des différences absolues de différents alignements d’byte entre la valeur de référence et la valeur source.

## <a name="requirements"></a>Spécifications

**En-tête:** amp_graphics.h

**Espace nom:** Concordance::graphiques::direct3d

## <a name="see-also"></a>Voir aussi

[Concordance::graphiques::direct3d Namespace](concurrency-graphics-direct3d-namespace.md)
