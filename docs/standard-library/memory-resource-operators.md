---
description: 'En savoir plus sur les opérateurs suivants : &lt; memory_resource &gt;'
title: '&lt;&gt;opérateurs memory_resource'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: 28c1dee4e2f022cdba14b7f71e7b9a2e40bc1162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183839"
---
# <a name="ltmemory_resourcegt-operators"></a>&lt;&gt;opérateurs memory_resource

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l’objet memory_resource situé à gauche de l’opérateur n’est pas égal à l’objet memory_resource situé à droite.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet memory_resource situé à gauche de l’opérateur est égal à l’objet memory_resource situé à droite.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
