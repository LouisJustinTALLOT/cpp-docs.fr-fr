---
description: 'En savoir plus sur : Concurrency :: Graphics ::d irect3d, fonctions de l’espace de noms'
title: Concurrency::graphics::direct3d, fonctions de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 52556835c843744e03661b3ef5b718c884765c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122354"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d, fonctions de l’espace de noms

:::row:::
   :::column span="":::
      [`get_sampler`](#get_sampler)\
      [`get_texture`](#get_texture)
   :::column-end:::
   :::column span="":::
      [`make_sampler`](#make_sampler)
   :::column-end:::
   :::column span="":::
      [`make_texture`](#make_texture)
   :::column-end:::
   :::column span="":::
      [`msad4`](#msad4)
   :::column-end:::
:::row-end:::

## <a name="get_sampler"></a><a name="get_sampler"></a> get_sampler

Obtient l’interface d’état de l’échantillonneur D3D sur la vue d’accélérateur donnée qui représente l’objet d’échantillonnage spécifié.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Vue d’accélérateur D3D sur laquelle l’état de l’échantillonneur D3D doit être créé.

*_Sampler*<br/>
Objet échantillonneur pour lequel l’interface d’état d’échantillonnage D3D sous-jacente est créée.

### <a name="return-value"></a>Valeur renvoyée

Pointeur d’interface IUnknown correspondant à l’état de l’échantillonneur D3D qui représente l’échantillonneur donné.

## <a name="get_texture"></a><a name="get_texture"></a> get_texture

Obtient l’interface de texture Direct3D sous-jacente à l’objet de [texture](texture-class.md) spécifié.

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
Type d’élément de la texture.

*_Rank*<br/>
Rang de la texture.

*_Texture*<br/>
Une texture ou une vue de texture associée au accelerator_view pour lequel l’interface de texture Direct3D sous-jacente est retournée.

### <a name="return-value"></a>Valeur renvoyée

Pointeur d’interface IUnknown correspondant à la texture Direct3D sous-jacente à la texture.

## <a name="make_sampler"></a><a name="make_sampler"></a> make_sampler

Créez un échantillonneur à partir d’un pointeur d’interface d’état d’échantillonnage D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_D3D_sampler*<br/>
Pointeur d’interface IUnknown de l’état de l’échantillonneur D3D à partir duquel créer l’échantillonneur.

### <a name="return-value"></a>Valeur renvoyée

Un échantillonneur représente l’état de l’échantillonneur D3D fourni.

## <a name="make_texture"></a><a name="make_texture"></a> make_texture

Crée un objet de [texture](texture-class.md) à l’aide des paramètres spécifiés.

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
Type des éléments de la texture.

*_Rank*<br/>
Rang de la texture.

*_Av*<br/>
Vue d’accélérateur D3D sur laquelle la texture doit être créée.

*_D3D_texture*<br/>
Pointeur d’interface IUnknown de la texture D3D à partir de laquelle créer la texture.

*_View_format*<br/>
Format DXGI à utiliser pour les vues créées à partir de cette texture. Transmettez DXGI_FORMAT_UNKNOWN (valeur par défaut) pour dériver le format du format sous-jacent de _D3D_texture et la value_type de ce modèle. Le format fourni doit être compatible avec le format sous-jacent de _D3D_texture.

### <a name="return-value"></a>Valeur renvoyée

Texture à l’aide de la texture D3D fournie.

## <a name="msad4"></a><a name="msad4"></a> msad4

Compare une valeur de référence de 4 octets et une valeur source de 8 octets et accumule un vecteur de 4 sommes. Chaque somme correspond à la somme masquée de différences absolues d’alignements d’octets différents entre la valeur de référence et la valeur source.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Reference*<br/>
Tableau de référence de 4 octets dans une valeur uint

*_Source*<br/>
Tableau source de 8 octets dans un vecteur de deux valeurs uint.

*_Accum*<br/>
Vecteur de 4 valeurs à ajouter à la somme masquée de différences absolues des différents alignements d’octets entre la valeur de référence et la valeur source.

### <a name="return-value"></a>Valeur renvoyée

Retourne un vecteur de 4 sommes. Chaque somme correspond à la somme masquée de différences absolues d’alignements d’octets différents entre la valeur de référence et la valeur source.

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency :: Graphics ::d irect3d

## <a name="see-also"></a>Voir aussi

[Concurrency :: Graphics ::d espace de noms irect3d](concurrency-graphics-direct3d-namespace.md)
