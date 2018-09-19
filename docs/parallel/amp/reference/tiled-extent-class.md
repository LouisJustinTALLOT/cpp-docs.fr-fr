---
title: tiled_extent, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d0a0606e531b4343bf8b5569daa5034c827dcb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114551"
---
# <a name="tiledextent-class"></a>tiled_extent, classe
Un `tiled_extent` objet est un `extent` objet d’une à trois dimensions qui subdivise l’espace d’extent en une, deux ou vignettes en trois dimensions.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <
    int _Dim0,  
    int _Dim1,  
    int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
 
template <
    int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
```  
  
### <a name="parameters"></a>Paramètres  
*_Dim0*<br/>
La longueur de la dimension la plus significative.  
  
*_Dim1*<br/>
La longueur de la prochaine-à-dimension la plus significative.  
  
*_Dim2*<br/>
La longueur de la dimension la moins significative.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[tiled_extent, constructeur](#ctor)|Initialise une nouvelle instance de la classe `tiled_extent`.|  

  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[get_tile_extent](#get_tile_extent)|Retourne un `extent` objet qui capture les valeurs de la `tiled_extent` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.|  
|[pad](#pad)|Retourne un nouvel `tiled_extent` objet avec les étendues ajustée inscrire pour être également divisibles par les dimensions de la vignette.|  
|[truncate](#truncate)|Retourne un nouvel `tiled_extent` objet avec les étendues sous-ajustées pour être également divisibles par les dimensions de la vignette.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator=](#operator_eq)|Copie le contenu de l’objet `tiled_index` objet dans celui-ci.|  

  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[tile_dim0 (constante)](#tile_dim0)|Stocke la longueur de la dimension la plus significative.|  
|[tile_dim1 (constante)](#tile_dim1)|Stocke la longueur de la prochaine-à-dimension la plus significative.|  
|[tile_dim2 (constante)](#tile_dim2)|Stocke la longueur de la dimension la moins significative.|  

  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Obtient un `extent` objet qui capture les valeurs de la `tiled_extent` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** amp.h  
  
 **Espace de noms :** Concurrency  

## <a name="ctor"> </a>  tiled_extent, constructeur  
Initialise une nouvelle instance de la classe `tiled_extent`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent();  
  
tiled_extent(  
    const Concurrency::extent<rank>& _Other );  
  
tiled_extent(  
    const tiled_extent& _Other );  
```  
  
### <a name="parameters"></a>Paramètres  
*_Autre*<br/>
Le `extent` ou `tiled_extent` objet à copier.  
  

  

## <a name="get_tile_extent"> </a>  get_tile_extent   
Retourne un `extent` objet qui capture les valeurs de la `tiled_extent` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `extent` objet qui capture les dimensions de ce `tiled_extent` instance.  
  

## <a name="pad"> </a>  remplissage   
Retourne un nouvel `tiled_extent` objet avec les étendues ajustée inscrire pour être également divisibles par les dimensions de la vignette.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La nouvelle `tiled_extent` objet, par valeur. 
## <a name="truncate"> </a>  tronquer   
Retourne un nouvel `tiled_extent` objet avec les étendues sous-ajustées pour être également divisibles par les dimensions de la vignette.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un nouvel `tiled_extent` objet avec les étendues sous-ajustées pour être également divisibles par les dimensions de la vignette.  

## <a name="operator_eq"> </a>  opérateur =   
Copie le contenu de l’objet `tiled_index` objet dans celui-ci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>Paramètres  
*_Autre*<br/>
Le `tiled_index` objet à copier.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à cet `tiled_index` instance.  

## <a name="tile_dim0"> </a>  tile_dim0   
Stocke la longueur de la dimension la plus significative.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tile_dim1"> </a>  tile_dim1   
Stocke la longueur de la prochaine-à-dimension la plus significative.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tile_dim2"> </a>  tile_dim2   
Stocke la longueur de la dimension la moins significative.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tile_extent"> </a>  tile_extent   
  Obtient un `extent` objet qui capture les valeurs de la `tiled_extent` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
