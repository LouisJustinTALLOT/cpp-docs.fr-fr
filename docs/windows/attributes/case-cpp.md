---
title: case (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: e1d3c113c42be99a8475c5a667b7ea6ed9583d92
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838904"
---
# <a name="case-c"></a>cas (C++)

Utilisé avec l’attribut [switch_type](switch-type.md) dans un **`union`** .

## <a name="syntax"></a>Syntaxe

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Paramètres

*value*<br/>
Une valeur d’entrée possible pour laquelle vous souhaitez fournir le traitement. Le type de **valeur** peut être l’un des types suivants :

- **`int`**

- **`char`**

- `boolean`

- **`enum`**

ou un identificateur de ce type.

## <a name="remarks"></a>Notes

L’attribut C++ de **cas** a les mêmes fonctionnalités que l’attribut MIDL de **cas** . Cet attribut est utilisé uniquement avec l’attribut [switch_type](switch-type.md) .

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

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Membre d’un **`class`** ou **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
