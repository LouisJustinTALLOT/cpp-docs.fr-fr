---
title: texture_view, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3db02d9cafb87c0f173546687ad01390e09b9f68
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696264"
---
# <a name="textureview-class"></a>texture_view, classe
Fournit l’accès en lecture et écriture à une texture. `texture_view` peut uniquement être utilisé pour lire les textures dont le type valeur est `int`, `unsigned int`, ou `float` qui ont bpse de 32 bits par défaut. Pour lire d’autres formats de texture, utilisez `texture_view<const value_type, _Rank>`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename value_type,int _Rank>  
class texture_view;  
 
template<typename value_type, int _Rank>  
class texture_view 
   : public details::_Texture_base<value_type, _Rank>;  
 
template<typename value_type, int _Rank>  
class texture_view<const value_type, _Rank> 
   : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value_type`  
 Le type des éléments dans l’agrégat de texture.  
  
 `_Rank`  
 Le classement de la `texture_view`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`value_type`|Le type des éléments dans les agrégats de texture.|  
|`coordinates_type`|Le type de la coordonnée permet de spécifier un texel dans le `texture_view`: autrement dit, un `short_vector` qui a le même rang que la texture associé qui a un type de valeur `float`.|  
|`gather_return_type`|Le type de retour utilisé pour collecter des opérations, autrement dit, un rang 4 `short_vector` que contient les quatre composants de couleur homogène collectées à partir des quatre valeurs texel échantillonnées.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[texture_view, constructeur](#ctor)|Surchargé. Construit un `texture_view` instance.|  
|[~ texture_view, destructeur](#ctor)|Détruit le `texture_view` instance.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants alpha (w) de quatre texels échantillonnées.|  
|[gather_blue](#gather_blue)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants bleu (z) de quatre texels échantillonnées.|  
|[gather_green](#gather_green)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants vert (y) de quatre texels échantillonnées.|  
|[gather_red](#gather_red)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants rouge (x) de quatre texels échantillonnées.|  
|[get](#get)|Surchargé. Obtient la valeur de l’élément par index.|  
|[Exemple](#sample)|Surchargé. Exemples de la texture au niveau de détail et aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié.|  
|[set](#set)|Définit la valeur d’un élément par index.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator()](#operator_call)|Surchargé. Obtient la valeur de l’élément par index.|  
|[operator[]](#operator_at)|Surchargé. Obtient la valeur de l’élément par index.|  
|[operator=](#operator_eq)|Surchargé. Opérateur d'assignation.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[value_type](#value_type)|Le type de valeur des éléments de la `texture_view`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_Texture_base`  
  
 `texture_view`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_graphics.h  
  
 **Namespace :** concurrency::graphics  
  
##  <a name="dtor"></a> ~ texture_view 

 Détruit le `texture_view` instance.  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="ctor"></a> texture_view 

 Construit un `texture_view` instance.  
  
```  
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
 `_Src`  
 [1, 2] Constructeur  
 Le `texture` sur lequel l’accessible en écriture `texture_view` est créé.  
  
 [3, 4] Constructeur  
 Le `texture` sur lequel la non inscriptibles `texture_view` est créé.  
  
 `_Other`  
 [5] constructeur de copie  
 La source accessible en écriture `texture_view`.  
  
 [6, 7] Constructeur de copie  
 La source non inscriptibles `texture_view`.  
  
 `_Mipmap_level`  
 Le niveau de mipmap spécifique sur la source de `texture` que ce accessible en écriture `texture_view` lie à. La valeur par défaut est 0, ce qui représente le niveau mip de niveau supérieur (plus détaillé).  
  
 `_Most_detailed_mip`  
 Haut niveau mip de niveau (plus détaillé) pour l’affichage, par rapport à l’élément spécifié `texture_view` objet.  
  
 `_Mip_levels`  
 Le nombre de niveaux de mipmap accessibles via la `texture_view`.  
  
##  <a name="gather_red"></a> gather_red 

 Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants rouge (x) de quatre texels échantillonnées.  
  
```  
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
 `_Address_mode`  
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est identique pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillonneur à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées pour prendre l’exemple à partir de. Les valeurs de coordonnées fractions de seconde sont utilisées pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 qui contient le composant rouge (x) de 4 échantillonnées valeurs texel.  
  
##  <a name="gather_green"></a> gather_green 

 Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants vert (y) de quatre texels échantillonnées.  
  
```  
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
 `_Address_mode`  
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est identique pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillonneur à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées pour prendre l’exemple à partir de. Les valeurs de coordonnées fractions de seconde sont utilisées pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 qui contient le composant vert (y) de 4 échantillonnées valeurs texel.  
  
##  <a name="gather_blue"></a> gather_blue 

 Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants bleu (z) de quatre texels échantillonnées.  
  
```  
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
 `_Address_mode`  
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est identique pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillonneur à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées pour prendre l’exemple à partir de. Les valeurs de coordonnées fractions de seconde sont utilisées pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 qui contient le composant rouge (x) de 4 échantillonnées valeurs texel.  
  
##  <a name="gather_alpha"></a> gather_alpha 

 Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants alpha (w) de quatre texels échantillonnées.  
  
```  
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
 `_Address_mode`  
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est identique pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillonneur à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées pour prendre l’exemple à partir de. Les valeurs de coordonnées fractions de seconde sont utilisées pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un rang égal à 4 court du vecteur qui contient la valeur alpha (w) composant 4 échantillonnées valeurs texel.  
  
##  <a name="get"></a> Télécharger 

 Obtient la valeur de l’élément à l’index spécifié.  
  
```  
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

 
value_type get(
    const index<_Rank>& _Index,  
    unsigned int _Mip_level = 0) const restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 Index de l’élément à obtenir, éventuellement à plusieurs dimensions.  
  
 `_Mip_level`  
 Le niveau de mipmap à partir de laquelle nous devrions obtenir la valeur. La valeur par défaut 0 représente le niveau de mipmap le plus détaillé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de l'élément.  
  
##  <a name="operator_eq"></a> opérateur = 

 Assigne une vue de la même texture comme spécifié `texture_view` à ce `texture_view` instance.  
  
```  
texture_view<value_type, _Rank>& operator= (// [1] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view<const value_type, _Rank>& operator= (// [2] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

 
texture_view<const value_type, _Rank>& operator= (// [3] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 [1, 2] Constructeur de copie  
 Un inscriptible `texture_view` objet.  
  
 [3] constructeur de copie  
 Non inscriptibles `texture_view` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `texture_view` instance.  
  
##  <a name="operator_at"></a> operator] 

 Retourne la valeur de l’élément par index.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);

 
value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 L’index, éventuellement à plusieurs dimensions.  
  
 `_I0`  
 L’index de dimension.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de l’élément indexé par `_Index`.  
  
##  <a name="operator_call"></a> operator() 

 Retourne la valeur de l’élément par index.  
  
```  
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
 `_Index`  
 L’index, éventuellement à plusieurs dimensions.  
  
 `_I0`  
 Le composant plus significatif de l’index.  
  
 `_I1`  
 Le composant suivant-à-plus significatif de l’index.  
  
 `_I2`  
 Le composant de poids de l’index.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de l’élément indexé par `_Index`.  
  
##  <a name="sample"></a> Exemple 

 Exemples de la texture au niveau de détail et aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié.  
  
```  
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
 `_Filter_mode`  
 Le mode de filtre à utiliser pour échantillonner le texture_view. Le mode de filtre est la même pour la minimisation, optimisation et les filtres de mipmap.  
  
 `_Address_mode`  
 Le mode d’adresse à utiliser pour échantillonner le texture_view. Le mode d’adresse est identique pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillonneur à utiliser pour échantillonner le texture_view.  
  
 `_Coord`  
 Les coordonnées pour prendre l’exemple à partir de. Les valeurs de coordonnées fractions de seconde sont utilisées pour l’interpolation entre les valeurs texel.  
  
 `_Level_of_detail`  
 La valeur spécifie le niveau de mipmap à échantillonner dans. Valeurs fractionnaires sont utilisées pour l’interpolation entre deux niveaux de mipmap. Le niveau de détail par défaut est 0, qui représente le niveau de mipmap le plus détaillé.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur interpolée d’exemple.  
  
##  <a name="set"></a> Ensemble 

 Définit la valeur de l’élément à l’index spécifié à la valeur spécifiée.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 Index de l’élément à définir éventuellement multidimensionnel.  
  
 `value`  
 Valeur à l’élément.  
  
##  <a name="value_type"></a> Value_type 

 Le type de valeur des éléments de la texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
