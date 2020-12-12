---
description: 'En savoir plus sur : classe writeonly_texture_view'
title: writeonly_texture_view, classe
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 17e9ed49c5fb3c976343d8c3ad8690d7f41b166d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314515"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view, classe

Fournit un accès WriteOnly à une texture.

## <a name="syntax"></a>Syntaxe

```cpp
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

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type des éléments de la texture.

*_Rank*<br/>
Rang de la texture.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Type des éléments de la texture.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur writeonly_texture_view](#ctor)|Initialise une nouvelle instance de la classe `writeonly_texture_view`.|
|[Destructeur ~ writeonly_texture_view](#ctor)|Détruit l' `writeonly_texture_view` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[set](#set)|Définit la valeur de l’élément à l’index spécifié.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Copie l’objet spécifié dans celui- `writeonly_texture_view` ci.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Obtient le rang de l' `writeonly_texture_view` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency :: Graphics

## <a name="writeonly_texture_view"></a><a name="dtor"></a> ~ writeonly_texture_view

Détruit l' `writeonly_texture_view` objet.

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

Copie l’objet spécifié dans celui- `writeonly_texture_view` ci.

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
`writeonly_texture_view` objet à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Référence à cet `writeonly_texture_view` objet.

## <a name="rank"></a><a name="rank"></a> moteurs

Obtient le rang de l' `writeonly_texture_view` objet.

```cpp
static const int rank = _Rank;
```

## <a name="set"></a><a name="set"></a> définie

Définit la valeur de l’élément à l’index spécifié.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l'élément.

*value*<br/>
Nouvelle valeur de l’élément.

## <a name="writeonly_texture_view"></a><a name="ctor"></a> writeonly_texture_view

Initialise une nouvelle instance de la classe `writeonly_texture_view`.

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang de la texture.

*value_type*<br/>
Type des éléments de la texture.

*_Src*<br/>
Texture utilisée pour créer le `writeonly_texture_view` .

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
