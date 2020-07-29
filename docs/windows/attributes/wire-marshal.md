---
title: wire_marshal (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.wire_marshal
helpviewer_keywords:
- wire_marshal attribute
ms.assetid: 244f9d72-776d-4ebd-b60a-cee600a126b5
ms.openlocfilehash: ff01d20117e2f04aca96b0fee7489d7195cc7488
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213773"
---
# <a name="wire_marshal"></a>wire_marshal

Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifique à l’application.

## <a name="syntax"></a>Syntaxe

```cpp
[wire_marshal]
```

## <a name="remarks"></a>Notes

L’attribut C++ **wire_marshal** a les mêmes fonctionnalités que l’attribut MIDL [wire_marshal](/windows/win32/Midl/wire-marshal) .

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de **wire_marshal**:

```cpp
// cpp_attr_ref_wire_marshal.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export, public] typedef unsigned long _FOUR_BYTE_DATA;

[export] typedef struct _TWO_X_TWO_BYTE_DATA {
   unsigned short low;
   unsigned short high;
} TWO_X_TWO_BYTE_DATA ;

[export, wire_marshal(TWO_X_TWO_BYTE_DATA)] typedef _FOUR_BYTE_DATA FOUR_BYTE_DATA;
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`typedef`**|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
