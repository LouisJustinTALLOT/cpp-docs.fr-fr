---
title: cas (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89a8479564048ec7313fee17a444f3e8d34443b0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790969"
---
# <a name="case-c"></a>cas (C++)

Utilisé avec le [switch_type](switch-type.md) d’attribut dans un **union**.

## <a name="syntax"></a>Syntaxe

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Paramètres

*valeur*<br/>
Une valeur d’entrée possible pour lequel vous souhaitez fournir un traitement. Le type de **valeur** peut être un des types suivants :

- `int`

- `char`

- `boolean`

- `enum`

un identificateur ou d’un tel type.

## <a name="remarks"></a>Notes

Le **cas** attribut C++ a les mêmes fonctionnalités que le **cas** attribut MIDL. Cet attribut est utilisé uniquement avec le [switch_type](switch-type.md) attribut.

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de la **cas** attribut :

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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Membre d’un **classe** ou **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)  