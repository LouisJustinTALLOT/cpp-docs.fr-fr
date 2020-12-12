---
description: 'En savoir plus sur : classe is_trivially_copy_constructible'
title: is_trivially_copy_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: c247e81f52ad98e546a840bb38938fe15bc9b302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118522"
---
# <a name="is_trivially_copy_constructible-class"></a>is_trivially_copy_constructible, classe

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

Un constructeur de copie pour une classe *T* est trivial s’il est déclaré implicitement, la classe *t* n’a pas de fonctions virtuelles ou de bases virtuelles, toutes les bases directes de la classe *T* ont des constructeurs de copie trivial, les classes de tous les membres de données non statiques de type classe ont des constructeurs de copie trivial et les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs de copie trivial.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
