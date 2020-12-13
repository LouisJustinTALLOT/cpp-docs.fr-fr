---
description: 'En savoir plus sur &lt; : &gt; énumérations de mémoire'
title: '&lt;memory&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: da9bb22a6095f74b94e1745210fa55061ecf3c71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149095"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt;, énumérations

## <a name="pointer_safety-enumeration"></a><a name="pointer_safety"></a> Énumération pointer_safety

Énumération des valeurs possibles retournées par `get_pointer_safety`.

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Notes

L’étendue **`enum`** définit les valeurs qui peuvent être retournées par `get_pointer_safety()` :

`relaxed` : les pointeurs qui ne sont pas dérivés de manière sécurisée (pointeurs vers des objets d’alloués ou déclarés) sont traités comme ceux qui sont dérivés de manière sécurisée.

`preferred` : comme avant, mais les pointeurs qui ne sont pas dérivés de manière sécurisée ne doivent pas être déréférencés.

`strict` : les pointeurs qui ne sont pas dérivés de manière sécurisée peuvent être traités différemment de ceux qui sont dérivés de manière sécurisée.
