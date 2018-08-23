---
title: '&lt;new&gt;, typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: bbfe7d2c24cb589925c70c70235f6de112d274f1
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42539654"
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
