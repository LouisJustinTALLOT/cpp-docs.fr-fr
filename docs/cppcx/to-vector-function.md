---
title: to_vector (fonction)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: 4fa4e9c620519cc6bb2f96d346ded88b6cc826ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404622"
---
# <a name="tovector-function"></a>to_vector (fonction)

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

### <a name="return-value"></a>Valeur de retour

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows::Foundation::Collections, espace de noms](../cppcx/windows-foundation-collections-namespace-c-cx.md)
