---
title: norm, classe
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447525"
---
# <a name="norm-class"></a>norm, classe

Représente un nombre normal. Chaque élément est un nombre à virgule flottante dans la plage de [-1.0 f, 1.0 f].

## <a name="syntax"></a>Syntaxe

```cpp
class norm;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur normal](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0.0 f.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|normal :: Operator-||
|normal :: Operator--||
|normal :: operator float|Opérateur de conversion. Convertit le nombre normal en valeur à virgule flottante.|
|norm::operator*=||
|normal :: Operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|normal :: Operator-=||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`norm`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="ctor"></a>rendement

Constructeur par défaut. Initialiser à 0.0 f.

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Paramètres

*_V*<br/>
Valeur utilisée pour initialiser.

*_Other*<br/>
Objet utilisé pour initialiser.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
