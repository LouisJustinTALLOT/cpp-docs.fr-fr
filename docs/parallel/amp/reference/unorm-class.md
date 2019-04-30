---
title: unorm, classe
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 059cd3a388d67e540a91146f2a287c375fb02bd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405428"
---
# <a name="unorm-class"></a>unorm, classe

Représente un nombre unorm. Chaque élément est flottante nombre à virgule dans la plage [0.0f, 1.0f].

## <a name="syntax"></a>Syntaxe

```
class unorm;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[unorm, constructeur](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0,0 f.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|unorm::operator--||
|unorm::operator float|Opérateur de conversion. Convertissez le nombre d’unorm flottante valeur de point.|
|unorm::operator*=||
|unorm::operator/=||
|unorm::operator++||
|unorm::operator+=||
|unorm::operator=||
|unorm::operator-=||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`unorm`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Espace de noms :** Concurrency::graphics

##  <a name="ctor"></a> unorm

Constructeur par défaut. Initialiser à 0,0 f.

```
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Paramètres

*_V*<br/>
La valeur utilisée pour initialiser.

*_Other*<br/>
L’objet de la norme utilisée pour initialiser.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
