---
title: allocator&lt;void&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: c8d787fe03dfe6f67fb8e228308ec74b6e7f620a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688530"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt;, classe

Spécialisation de l’allocateur de modèle de classe en type **void**, définissant les types qui ont un sens dans ce contexte.

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

La classe spécialise explicitement l' [allocateur](../standard-library/allocator-class.md) de modèle de classe pour le type **void**. Ses constructeurs et son opérateur d’assignation se comportent de la même façon que pour le modèle de classe, mais il définit uniquement les types suivants :

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [pointer](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- une [reliaison](../standard-library/allocator-class.md#rebind), modèle de classe imbriquée.
