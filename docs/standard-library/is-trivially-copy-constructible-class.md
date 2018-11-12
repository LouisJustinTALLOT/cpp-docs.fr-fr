---
title: is_trivially_copy_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: aa6d6b19ae2bd5d6967c57db61c5697c0c6153e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630514"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible, classe

Teste si le type a un constructeur de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est une classe qui a un constructeur de copie triviaux, sinon, sa valeur est false.

Un constructeur de copie pour une classe *T* est trivial s’il est implicitement déclaré, la classe *T* n’a pas les fonctions virtuelles ni les bases virtuelles, toutes les bases directes de classe *T* ont constructeurs de copie triviaux, les classes de tous les membres de données non statiques de type de classe possèdent des constructeurs de copie triviaux, et les classes de tous les membres de données non statiques de type tableau de classe possèdent des constructeurs de copie trivial.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
