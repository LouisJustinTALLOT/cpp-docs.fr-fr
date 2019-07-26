---
title: is_trivially_copy_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447991"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible, classe

Teste si le type a un constructeur de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est une classe qui a un constructeur de copie trivial. sinon, sa valeur est false.

Un constructeur de copie pour une classe *t* est trivial s’il est déclaré implicitement, la classe *t* n’a pas de fonctions virtuelles ou de bases virtuelles, toutes les bases directes de la classe *t* ont des constructeurs de copie trivial, les classes de tous les membres de données non statiques de type classe ont des constructeurs de copie trivial, et les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs de copie trivial.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
