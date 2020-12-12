---
description: 'En savoir plus sur : fonction to_vector'
title: to_vector (fonction)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: 77d6bee58a793946f91bc03ba4afed35aa7252cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307585"
---
# <a name="to_vector-function"></a>to_vector (fonction)

Retourne un `std::vector` dont la valeur est la même que la collection sous-jacente du paramètre IVector ou IVectorView spécifié.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de type de modèle.

*v*<br/>
Interface IVector ou IVectorView qui permet d'accéder à un objet Vector ou VectorView sous-jacent.

### <a name="return-value"></a>Valeur renvoyée

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows :: Foundation :: Collections, espace de noms](../cppcx/windows-foundation-collections-namespace-c-cx.md)
