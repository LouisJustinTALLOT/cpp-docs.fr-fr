---
title: unorm, classe
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 7c9ec967be8be618e5f8ab3bad1bfd940bfeaef4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126303"
---
# <a name="unorm-class"></a>unorm, classe

Représente un numéro unorm. Chaque élément est un nombre à virgule flottante dans la plage de [0.0 f, 1.0 f].

## <a name="syntax"></a>Syntaxe

```cpp
class unorm;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur unorm](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0.0 f.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|unorm :: Operator--||
|unorm :: operator float|Opérateur de conversion. Convertit le nombre unorm en valeur à virgule flottante.|
|unorm::operator*=||
|unorm :: Operator/=||
|unorm :: Operator + +||
|unorm::operator+=||
|unorm::operator=||
|unorm :: Operator-=||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`unorm`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="ctor"></a>unorm

Constructeur par défaut. Initialiser à 0.0 f.

```cpp
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
Valeur utilisée pour initialiser.

*_Other*<br/>
Objet normal utilisé pour initialiser.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
