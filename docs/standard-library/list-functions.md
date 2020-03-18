---
title: '&lt;de la liste des&gt; fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420063"
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
