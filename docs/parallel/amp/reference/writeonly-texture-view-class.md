---
title: writeonly_texture_view, classe
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 5244ae5df99b06c77f4eb27317e5829b21fabf24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405415"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view, classe

Fournit un accès à une texture writeonly.

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

*value_type*<br/>
Le type des éléments de la texture.

*_Rank*<br/>
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

|Nom|Description|
|----------|-----------------|
|[rang (constante)](#rank)|Obtient le rang de le `writeonly_texture_view` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_graphics.h

**Espace de noms :** Concurrency::graphics

##  <a name="dtor"></a> ~writeonly_texture_view

Détruit le `writeonly_texture_view` objet.

```
~writeonly_texture_view() restrict(amp,cpu);
```

##  <a name="operator_eq"></a> operator=

Copie le texte spécifié `writeonly_texture_view` objet à celui-ci.

```
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
`writeonly_texture_view` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `writeonly_texture_view` objet.

##  <a name="rank"></a> rang

Obtient le rang de le `writeonly_texture_view` objet.

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

*_Index*<br/>
L’index de l’élément.

*value*<br/>
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

*_Rank*<br/>
Le rang de la texture.

*value_type*<br/>
Le type des éléments de la texture.

*_Src*<br/>
La texture est utilisée pour créer le `writeonly_texture_view`.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
