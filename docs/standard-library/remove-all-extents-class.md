---
description: 'En savoir plus sur : classe remove_all_extents'
title: remove_all_extents, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_all_extents
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
ms.openlocfilehash: a6c798e1f128b10ef94061573c93c3bb9e3aa4f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159724"
---
# <a name="remove_all_extents-class"></a>remove_all_extents, classe

Convertit un type tableau en un type autre qu'un type tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_all_extents;

template <class T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_all_extents<T>` contient un type modifié qui est le type d’élément du type tableau *T* avec toutes les dimensions de tableau supprimées, ou *t* si *t* n’est pas un type tableau.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_all_extents<int> == "
        << typeid(std::remove_all_extents_t<int>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5]> == "
        << typeid(std::remove_all_extents_t<int[5]>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5][10]> == "
        << typeid(std::remove_all_extents_t<int[5][10]>).name()
        << std::endl;

    return (0);
    }
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe remove_extent](../standard-library/remove-extent-class.md)
