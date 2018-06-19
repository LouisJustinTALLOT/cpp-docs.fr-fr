---
title: writeonly_texture_view, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6b1bc5c90fd837f56dbd98eddb37f624e78080b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695403"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view, classe
Fournit l’accès writeonly une texture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view;  
 
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value_type`  
 Le type des éléments de la texture.  
  
 `_Rank`  
 Le rang de la texture.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`scalar_type`||  
|`value_type`|Le type des éléments de la texture.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[writeonly_texture_view, constructeur](#ctor)|Initialise une nouvelle instance de la classe `writeonly_texture_view`.|  
|[~ writeonly_texture_view, destructeur](#ctor)|Détruit le `writeonly_texture_view` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[set](#set)|Définit la valeur de l’élément à l’index spécifié.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator=](#operator_eq)|Copie le texte spécifié `writeonly_texture_view` objet à celui-ci.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[RANK (constante)](#rank)|Obtient le classement de la `writeonly_texture_view` objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_graphics.h  
  
 **Namespace :** Concurrency::graphics  
  
##  <a name="dtor"></a> ~writeonly_texture_view 

 Détruit le `writeonly_texture_view` objet.  
  
```  
~writeonly_texture_view() restrict(amp,cpu);
```  
  
##  <a name="operator_eq"></a> opérateur = 

 Copie le texte spécifié `writeonly_texture_view` objet à celui-ci.  
  
```  
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 `writeonly_texture_view` objet à copier à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `writeonly_texture_view` objet.  
  
##  <a name="rank"></a> Rang 

 Obtient le classement de la `writeonly_texture_view` objet.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="set"></a> Ensemble 

 Définit la valeur de l’élément à l’index spécifié.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 L’index de l’élément.  
  
 `value`  
 Nouvelle valeur de l’élément.  
  
##  <a name="ctor"></a> writeonly_texture_view 

 Initialise une nouvelle instance de la classe `writeonly_texture_view`.  
  
```  
writeonly_texture_view(
    texture<value_type, 
    _Rank>& _Src) restrict(amp);

 
writeonly_texture_view(
    const writeonly_texture_view<value_type,  
    _Rank>& _Src) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rank`  
 Le rang de la texture.  
  
 `value_type`  
 Le type des éléments de la texture.  
  
 `_Src`  
 La texture est utilisée pour créer le `writeonly_texture_view`.  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
