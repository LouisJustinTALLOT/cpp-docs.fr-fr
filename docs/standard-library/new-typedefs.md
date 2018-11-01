---
title: '&lt;new&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549118"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt;, typedefs

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

Le type pointe vers une fonction pouvant être utilisée comme gestionnaire new.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Notes

Ce type de fonction de gestionnaire est appelé par **operatornew** ou `operator new[]` quand ils ne peuvent pas satisfaire à une demande de stockage supplémentaire.

### <a name="example"></a>Exemple

Pour obtenir un exemple utilisant `new_handler` comme valeur de retour, consultez [set_new_handler](../standard-library/new-functions.md#set_new_handler).

## <a name="see-also"></a>Voir aussi

[\<new>](../standard-library/new.md)<br/>
