---
title: underlying_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 23e5e9bc5406265f49fca2ed220c597cb32e2a9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399360"
---
# <a name="underlyingtype-class"></a>underlying_type, classe

Génère le type intégral sous-jacent pour un type d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Le `type` typedef de membre de la classe de modèle désigne le type intégral sous-jacent de *T*, lorsque *T* est un type énumération, sinon il n’existe aucun typedef de membre `type`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
