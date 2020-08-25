---
title: switch_type (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: 0c39aa442c9d4eaf3a482e411cda762fe0cc34b3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838527"
---
# <a name="switch_type"></a>switch_type

Identifie le type de la variable utilisée en tant qu’Union discriminante.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Le type de commutateur peut être un type entier, caractère, booléen ou énumération.

## <a name="remarks"></a>Notes

L’attribut C++ **switch_type** a les mêmes fonctionnalités que l’attribut MIDL [switch_type](/windows/win32/Midl/switch-type) .

Les attributs C++ ne prennent pas en charge les [unions encapsulées](/windows/win32/Midl/encapsulated-unions). Les unions qui ne sont pas [encapsulées](/windows/win32/Midl/nonencapsulated-unions) sont prises en charge uniquement sous la forme suivante :

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

Pour obtenir un exemple d’utilisation de **switch_type**, consultez l’exemple de [cas](case-cpp.md) .

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`typedef`**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[exporter](export.md)
