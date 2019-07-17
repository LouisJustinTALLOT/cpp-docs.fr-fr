---
title: '&lt;liste&gt; fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269021"
---
# <a name="ltlistgt-functions"></a>&lt;liste&gt; fonctions

## <a name="swap"></a> échange

Échange les éléments de deux listes.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.
