---
title: texture_view, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 7d3206aea6a6f1e3033e157b3b99a6b3486cb2ac
ms.lasthandoff: 02/24/2017

---
# <a name="textureview-class"></a>texture_view, classe
Fournit l’accès en lecture et écriture à une texture. `texture_view`peut uniquement être utilisé pour lire les textures dont le type valeur est `int`, `unsigned int`, ou `float` qui ont bpse de 32 bits par défaut. Pour lire d’autres formats de texture, utilisez `texture_view<const value_type, _Rank>`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class texture_view;  
 
template <
    typename value_type,  
    int _Rank  
>  
class texture_view : public details::_Texture_base<value_type, _Rank>;  
 
template <
    typename value_type,  
    int _Rank  
>  
class texture_view<const value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;  
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
|`coordinates_type`|Le type de la coordonnée permet de spécifier un texel dans le `texture_view`, autrement dit, un `short_vector` qui a le même rang que la texture associé qui a un type de valeur de `float`.|  
|`gather_return_type`|Utilisé pour le type de retour rassembler des opérations, autrement dit, un rang 4 `short_vector` que contient les quatre composants de couleur homogènes collectées à partir des quatre valeurs texel échantillonnées.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[texture_view, constructeur](#ctor)|Surchargé. Construit un `texture_view` instance.|  
|[~ texture_view, destructeur](#ctor)|Détruit le `texture_view` instance.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[gather_alpha (méthode)](#gather_alpha)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants alpha (w) des quatre texels échantillonnées.|  
|[gather_blue (méthode)](#gather_blue)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants bleu (z) de quatre texels échantillonnées.|  
|[gather_green (méthode)](#gather_green)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants vert (y) de quatre texels échantillonnées.|  
|[gather_red (méthode)](#gather_red)|Surchargé. Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants rouge (x) de quatre texels échantillonnées.|  
|[Get (méthode)](#get)|Surchargé. Obtient la valeur de l’élément par index.|  
|[exemple de méthode](#sample)|Surchargé. Exemples de la texture au niveau de détail et aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié.|  
|[Set, méthode](#set)|Définit la valeur d’un élément par index.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator() (opérateur)](#operator__)|Surchargé. Obtient la valeur de l’élément par index.|  
|[operator [] (opérateur)](#operator_at)|Surchargé. Obtient la valeur de l’élément par index.|  
|[opérateur =, opérateur](#operator_eq)|Surchargé. Opérateur d'assignation.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Value_type (donnée membre)](#value_type)|Le type de valeur des éléments de la `texture_view`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `_Texture_base`  
  
 `texture_view`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_graphics.h  
  
 **Namespace :** concurrency::graphics  
  
##  <a name="a-namedtora-textureview"></a><a name="dtor"></a>~ texture_view 

 Détruit le `texture_view` instance.  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="a-namectora-textureview"></a><a name="ctor"></a>texture_view 

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
 Le `texture` sur lequel l’écriture `texture_view` est créé.  
  
 [3, 4] Constructeur  
 Le `texture` sur lequel la non inscriptibles `texture_view` est créé.  
  
 `_Other`  
 [5] constructeur de copie  
 La source accessible en écriture `texture_view`.  
  
 [6, 7] Constructeur de copie  
 La source non inscriptibles `texture_view`.  
  
 `_Mipmap_level`  
 Le niveau de mipmap spécifique sur la source de `texture` que ce inscriptible `texture_view` lie à. La valeur par défaut est 0, qui représente le niveau mip de niveau supérieur (le plus détaillé).  
  
 `_Most_detailed_mip`  
 Haut niveau mip de niveau (le plus détaillé) pour l’affichage, par rapport à l’élément spécifié `texture_view` objet.  
  
 `_Mip_levels`  
 Le nombre de niveaux de mipmap accessibles via la `texture_view`.  
  
##  <a name="a-namegatherreda-gatherred"></a><a name="gather_red"></a>gather_red 

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
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillon à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées à prendre l’exemple à partir de. Valeurs de coordonnées de fractions de seconde sont utilisés pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 contenant le composant rouge (x) de 4 valeurs texel l’échantillonnage.  
  
##  <a name="a-namegathergreena-gathergreen"></a><a name="gather_green"></a>gather_green 

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
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillon à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées à prendre l’exemple à partir de. Valeurs de coordonnées de fractions de seconde sont utilisés pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 contenant le composant vert (y) du 4 échantillonnées valeurs texel.  
  
##  <a name="a-namegatherbluea-gatherblue"></a><a name="gather_blue"></a>gather_blue 

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
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillon à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées à prendre l’exemple à partir de. Valeurs de coordonnées de fractions de seconde sont utilisés pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un vecteur court rang 4 contenant le composant rouge (x) de 4 valeurs texel l’échantillonnage.  
  
##  <a name="a-namegatheralphaa-gatheralpha"></a><a name="gather_alpha"></a>gather_alpha 

 Exemples de la texture aux coordonnées spécifiées à l’aide de la configuration d’échantillonnage spécifié et retourne les composants alpha (w) des quatre texels échantillonnées.  
  
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
 Le mode d’adresse à utiliser pour exemple le `texture_view`. Le mode d’adresse est le même pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillon à utiliser pour exemple le `texture_view`.  
  
 `_Coord`  
 Les coordonnées à prendre l’exemple à partir de. Valeurs de coordonnées de fractions de seconde sont utilisés pour l’interpolation entre les éléments de texture par exemple.  
  
### <a name="return-value"></a>Valeur de retour  
 Un rang égal à 4 court vecteur contenant la valeur alpha (s) composant 4 échantillonnées valeurs texel.  
  
##  <a name="a-namegeta-get"></a><a name="get"></a>Télécharger 

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
 Le niveau de mipmap à partir duquel nous devrions obtenir la valeur. La valeur par défaut 0 représente le niveau de mipmap le plus détaillé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de l'élément.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>opérateur = 

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
 Accessible en écriture `texture_view` objet.  
  
 [3] constructeur de copie  
 Non inscriptibles `texture_view` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `texture_view` instance.  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

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
  
##  <a name="a-nameoperatora-operator"></a><a name="operator__"></a>operator() 

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
  
##  <a name="a-namesamplea-sample"></a><a name="sample"></a>exemple 

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
 Le mode de filtre à utiliser pour échantillonner le texture_view. Le mode de filtrage est le même pour la minimisation, optimisation et des filtres de mipmap.  
  
 `_Address_mode`  
 Le mode d’adresse à utiliser pour échantillonner le texture_view. Le mode d’adresse est le même pour toutes les dimensions.  
  
 `_Sampler`  
 La configuration de l’échantillon à utiliser pour échantillonner le texture_view.  
  
 `_Coord`  
 Les coordonnées à prendre l’exemple à partir de. Valeurs de coordonnées de fractions de seconde sont utilisés pour l’interpolation entre les valeurs texel.  
  
 `_Level_of_detail`  
 La valeur spécifie le niveau de mipmap échantillonner. Les valeurs fractionnaires sont utilisées pour l’interpolation entre deux niveaux de mipmap. Le niveau de détail par défaut est 0, qui représente le niveau mip le plus détaillé.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur interpolée d’exemple.  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>ensemble 

 Définit la valeur de l’élément à l’index spécifié à la valeur spécifiée.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 Index de l’élément à définir, éventuellement à plusieurs dimensions.  
  
 `value`  
 La valeur de l’élément.  
  
##  <a name="a-namevaluetypea-valuetype"></a><a name="value_type"></a>Value_type 

 Le type de valeur des éléments de la texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency::Graphics Namespace](concurrency-graphics-namespace.md)

