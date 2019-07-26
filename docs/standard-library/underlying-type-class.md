---
title: underlying_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 465383357e6c0306c24fe8325327327c3a3b64c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454984"
---
# <a name="underlyingtype-class"></a>underlying_type, classe

Génère le type intégral sous-jacent pour un type d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Le `type` typedef de membre de la classe de modèle nomme le type intégral sous-jacent de *T*, quand *t* est un type d’énumération, `type`sinon il n’y a aucun typedef de membre.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
