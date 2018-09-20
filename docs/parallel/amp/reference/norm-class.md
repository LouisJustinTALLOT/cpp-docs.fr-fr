---
title: Norm, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs:
- C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 362ad3a2676fa1a7c8f965a6750782617d6a3203
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425728"
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
|Norm::operator-||
|Norm::operator--||
|Norm::operator float|Opérateur de conversion. Convertissez le nombre de norme flottante valeur de point.|
|Norm::operator * =||
|/ = Norm::operator||
|Norm::operator ++||
|Norm::operator +=||
|Norm::operator =||
|Norm::operator =||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`norm`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Namespace :** Concurrency::graphics

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

*_Autre*<br/>
L’objet utilisé pour initialiser.

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
