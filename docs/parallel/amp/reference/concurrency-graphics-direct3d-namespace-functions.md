---
title: Fonctions d’espace de noms Concurrency::Graphics::Direct3D | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed95ed8df8a42dc62684c71a3005c2f33fecd18
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686332"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Fonctions d’espace de noms Concurrency::Graphics::Direct3D
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>  get_sampler  
 Obtenir l’interface d’état D3D échantillonneur sur l’accélérateur donné afficher qui représente l’objet de l’échantillonneur spécifié.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Av`  
 Vue d’accélérateur D3D sur lequel l’état de l’échantillonneur D3D doit être créé.  
  
 `_Sampler`  
 Un objet d’échantillon pour lequel l’interface d’état D3D échantillonneur sous-jacent est créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur d’interface IUnknown correspondant à l’état de l’échantillonneur D3D qui représente l’échantillonneur donné.  
  
##  <a name="get_texture"></a>  get_texture  
 Obtient l’interface de texture Direct3D sous-jacent spécifié [texture](texture-class.md) objet.  
  
```  
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
 `value_type`  
 Le type d’élément de la texture.  
  
 `_Rank`  
 Le rang de la texture.  
  
 `_Texture`  
 Une texture ou une vue de texture associé à l’accelerator_view pour lequel l’interface de texture Direct3D sous-jacent est retourné.  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur d’interface IUnknown correspondant à la texture Direct3D sous-jacents de la texture.  
  
##  <a name="make_sampler"></a>  make_sampler  
 Créer un échantillon à partir d’un pointeur d’interface état D3D échantillonneur.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_D3D_sampler`  
 Pointeur d’interface IUnknown de l’état de l’échantillonneur D3D pour créer l’échantillonneur de.  
  
### <a name="return-value"></a>Valeur de retour  
 Un échantillon de représente l’état de l’échantillonneur D3D fourni.  
  
##  <a name="make_texture"></a>  make_texture  
 Crée un [texture](texture-class.md) objet en utilisant les paramètres spécifiés.  
  
```  
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
 `value_type`  
 Le type des éléments de la texture.  
  
 `_Rank`  
 Le rang de la texture.  
  
 `_Av`  
 Vue d’accélérateur D3D sur laquelle la texture doit être créé.  
  
 `_D3D_texture`  
 Pointeur d’interface IUnknown de la texture D3D pour créer la texture à partir de.  
  
 `_View_format`  
 Le format DXGI à utiliser pour les vues créées à partir de cette texture. Passez DXGI_FORMAT_UNKNOWN (la valeur par défaut) pour dériver le format sous-jacent du _D3D_texture et value_type de ce modèle dans le format. La mise en forme fournie doit être compatible avec le format sous-jacent du _D3D_texture.  
  
### <a name="return-value"></a>Valeur de retour  
 Une texture à l’aide de la texture D3D fournie.  
  
##  <a name="msad4"></a>  msad4  
 Compare une valeur de référence de 4 octets et une valeur de la source de 8 octets et accumule un vecteur de 4 sommes. Chaque somme correspond à la somme masquée des valeurs absolues des alignements d’octets différents entre la valeur de référence et la valeur de la source.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Reference`  
 Le tableau de référence de 4 octets dans une seule valeur uint  
  
 `_Source`  
 Le tableau de la source de 8 octets dans un vecteur de deux valeurs uint.  
  
 `_Accum`  
 Un vecteur de 4 valeurs à ajouter à la somme masquée des valeurs absolues des alignements octets différents entre la valeur de référence et la valeur de la source.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un vecteur de 4 sommes. Chaque somme correspond à la somme masquée des valeurs absolues des alignements d’octets différents entre la valeur de référence et la valeur de la source.  

## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_graphics.h  
  
 **Namespace :** Concurrency::graphics::direct3d 

## <a name="see-also"></a>Voir aussi  
 [Concurrency::graphics::direct3d, espace de noms](concurrency-graphics-direct3d-namespace.md)
