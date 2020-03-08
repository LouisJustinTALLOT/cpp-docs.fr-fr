---
title: '&lt;de la liste des&gt; fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874424"
---
# <a name="ltlistgt-functions"></a>&lt;de la liste des fonctions&gt;

## <a name="swap"></a>échange

Échange les éléments de deux listes.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `list`.

\ *droit*
Objet de type `list`.

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.
