---
title: allocator&lt;void&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 5591570527946895d1e0456b23327d7fabc4bef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646101"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt;, classe

Une spécialisation de la classe de modèle allocator en type **void**, définir les types qui sont pertinents dans ce contexte.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Notes

La classe spécialise explicitement la classe de modèle [allocateur](../standard-library/allocator-class.md) pour le type **void**. Ses constructeurs et l’opérateur d’assignation se comportent de la même façon que la classe de modèle, mais elle définit uniquement les types suivants :

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [pointer](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [rebind](../standard-library/allocator-class.md#rebind), une classe de modèle imbriquée.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
