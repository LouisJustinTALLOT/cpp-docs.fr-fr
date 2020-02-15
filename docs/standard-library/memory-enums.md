---
title: '&lt;memory&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257830"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt;, énumérations

## <a name="pointer_safety"></a>Énumération pointer_safety

Énumération des valeurs possibles retournées par `get_pointer_safety`.

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Notes

L' **énumération** délimitée définit les valeurs qui peuvent être retournées par `get_pointer_safety()`:

`relaxed` : les pointeurs qui ne sont pas dérivés de manière sécurisée (pointeurs vers des objets d’alloués ou déclarés) sont traités comme ceux qui sont dérivés de manière sécurisée.

`preferred` : comme avant, mais les pointeurs qui ne sont pas dérivés de manière sécurisée ne doivent pas être déréférencés.

`strict` : les pointeurs qui ne sont pas dérivés de manière sécurisée peuvent être traités différemment de ceux qui sont dérivés de manière sécurisée.
