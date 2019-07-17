---
title: '&lt;memory&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243846"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt;, énumérations

## <a name="pointer_safety"></a> pointer_safety, énumération

Énumération des valeurs possibles retournées par `get_pointer_safety`.

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Notes

L’étendue **enum** définit les valeurs qui peuvent être retournés par `get_pointer_safety()`:

`relaxed` : les pointeurs qui ne sont pas dérivés de manière sécurisée (pointeurs vers des objets d’alloués ou déclarés) sont traités comme ceux qui sont dérivés de manière sécurisée.

`preferred` : comme avant, mais les pointeurs qui ne sont pas dérivés de manière sécurisée ne doivent pas être déréférencés.

`strict` : les pointeurs qui ne sont pas dérivés de manière sécurisée peuvent être traités différemment de ceux qui sont dérivés de manière sécurisée.
