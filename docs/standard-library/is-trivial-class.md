---
title: is_trivial, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 609fdd9c3d0d00eea607db4aefd31163234a9a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526852"
---
# <a name="istrivial-class"></a>is_trivial, classe

Teste si le type est un type trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type trivial, sinon, sa valeur est false. Les types triviaux sont les types scalaires, les types de classes pouvant être copiés de façon triviale, les tableaux de ces types et les versions cv-qualified de ces types.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
