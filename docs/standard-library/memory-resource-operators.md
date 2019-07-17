---
title: '&lt;memory_resource&gt; opérateurs'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268901"
---
# <a name="ltmemoryresourcegt-operators"></a>&lt;memory_resource&gt; opérateurs

## <a name="op_neq"></a> opérateur ! =

Teste si l’objet memory_resource sur le côté gauche de l’opérateur n’est pas égal à l’objet memory_resource sur le côté droit.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a> operator==

Teste si l’objet memory_resource sur le côté gauche de l’opérateur est égal à l’objet memory_resource sur le côté droit.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
