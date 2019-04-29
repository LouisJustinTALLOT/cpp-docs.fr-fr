---
title: norm, classe
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351561"
---
# <a name="norm-class"></a>norm, classe

Représente un nombre de norme. Chaque élément est flottante nombre à virgule dans la plage [-1.0f, 1.0f].

## <a name="syntax"></a>Syntaxe

```
class norm;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Norm, constructeur](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0,0 f.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|Norm::operator float|Opérateur de conversion. Convertissez le nombre de norme flottante valeur de point.|
|norm::operator*=||
|norm::operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`norm`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Espace de noms :** Concurrency::graphics

##  <a name="ctor"></a> norme

Constructeur par défaut. Initialiser à 0,0 f.

```
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
La valeur utilisée pour initialiser.

*_Other*<br/>
L’objet utilisé pour initialiser.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
