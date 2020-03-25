---
title: case (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: da72fff3bb600b5db2fba0ecdfe9c6a768836f3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167333"
---
# <a name="case-c"></a>cas (C++)

Utilisé avec l’attribut [switch_type](switch-type.md) dans une **Union**.

## <a name="syntax"></a>Syntaxe

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Paramètres

*value*<br/>
Une valeur d’entrée possible pour laquelle vous souhaitez fournir le traitement. Le type de **valeur** peut être l’un des types suivants :

- `int`

- `char`

- `boolean`

- `enum`

ou un identificateur de ce type.

## <a name="remarks"></a>Notes

L’attribut **case** C++ a les mêmes fonctionnalités que l’attribut MIDL de **cas** . Cet attribut est utilisé uniquement avec l’attribut [switch_type](switch-type.md) .

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de l’attribut **case** :

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Membre d’une **classe** ou d’un **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
