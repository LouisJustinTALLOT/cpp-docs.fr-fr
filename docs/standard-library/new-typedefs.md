---
title: '&lt;new&gt;, typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 5ab0087a85cb2fce6fa300db136e7c60c66b0b5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852189"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt;, typedefs

||
|-|
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
