---
title: allocator&lt;void&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204928"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt;, classe

Spécialisation de l’allocateur de modèle de classe en type **`void`** , définissant les types qui ont un sens dans ce contexte.

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

La classe spécialise explicitement l' [allocation](allocator-class.md) de modèle de classe pour le type **`void`** . Ses constructeurs et son opérateur d’assignation se comportent de la même façon que pour le modèle de classe, mais il définit uniquement les types suivants :

- [const_pointer](allocator-class.md#const_pointer).

- [pointeur](allocator-class.md#pointer).

- [Value_type](allocator-class.md#value_type).

- une [reliaison](allocator-class.md#rebind), modèle de classe imbriquée.
