---
title: AgileActivationFactory, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
ms.openlocfilehash: 854f998e31cfec577fb6ff0fb3d82dc1499f88bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303833"
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory, classe

Représente une fabrique d’activation de cloisonnement conviviale qui implémente [FtmBase](ftmbase-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    FactoryCacheFlags cacheFlagValue = FactoryCacheDefault
>
class AgileActivationFactory :
    public ActivationFactory<
        Implements<FtmBase, I0>,
        I1,
        I2,
        cacheFlagValue
    >;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[ActivationFactory, classe](activationfactory-class.md)