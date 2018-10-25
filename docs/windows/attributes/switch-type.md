---
title: switch_type (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7aa11ada46f74c3e2a7293c65151b1f1ede7255e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080089"
---
# <a name="switchtype"></a>switch_type

Identifie le type de la variable utilisée en tant que l’union discriminante.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Le type de commutateur, peut être un type entier, caractère, booléen ou d’énumération.

## <a name="remarks"></a>Notes

Le **switch_type** attribut C++ a les mêmes fonctionnalités que le [switch_type](/windows/desktop/Midl/switch-type) attribut MIDL.

Attributs C++ ne gèrent pas [encapsulé unions](/windows/desktop/Midl/encapsulated-unions). [Unions nonencapsulated](/windows/desktop/Midl/nonencapsulated-unions) sont pris en charge uniquement sous la forme suivante :

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Exemple

Consultez le [cas](case-cpp.md) exemple pour un exemple d’utilisation de **switch_type**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)