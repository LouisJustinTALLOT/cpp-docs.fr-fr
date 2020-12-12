---
description: 'En savoir plus sur : classe de norme'
title: norm, classe
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 29e376e5e42212c87ae244c7a606a38d6a07ddf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327649"
---
# <a name="norm-class"></a>norm, classe

Représente un nombre normal. Chaque élément est un nombre à virgule flottante dans la plage de [-1.0 f, 1.0 f].

## <a name="syntax"></a>Syntaxe

```cpp
class norm;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur normal](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0.0 f.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|normal :: Operator-||
|normal :: Operator--||
|normal :: operator float|Opérateur de conversion. Convertit le nombre normal en valeur à virgule flottante.|
|normal :: Operator * =||
|normal :: Operator/=||
|norme :: Operator + +||
|norme :: Operator + =||
|norme :: Operator =||
|normal :: Operator-=||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`norm`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="norm"></a><a name="ctor"></a> rendement

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
