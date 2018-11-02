---
title: '&lt;forward_list&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: b425461f1428470b04a525efdd9a702ae038a283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477335"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt;, fonctions

||
|-|
|[swap](#swap)|

## <a name="swap"></a>  swap

Échange les éléments de deux forward_list.

```cpp
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*left*|Objet de type `forward_list`.|
|*right*|Objet de type `forward_list`.|

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.

## <a name="see-also"></a>Voir aussi

[<forward_list>](../standard-library/forward-list.md)<br/>
