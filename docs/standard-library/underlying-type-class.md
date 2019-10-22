---
title: underlying_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688841"
---
# <a name="underlying_type-class"></a>underlying_type, classe

Génère le type intégral sous-jacent pour un type d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Paramètres

*T* \
Type à modifier.

## <a name="remarks"></a>Notes

Le `type` membre typedef du modèle de classe nomme le type intégral sous-jacent de *t*, quand *t* est un type d’énumération, sinon il n’y a aucun typedef de membre `type`.

## <a name="requirements"></a>spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
