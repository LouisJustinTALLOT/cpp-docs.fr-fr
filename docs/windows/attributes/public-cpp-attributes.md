---
title: public (attributs C++) (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: d5307b96c58492aa06f115ca7a814aa221062e01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224368"
---
# <a name="public-c-attributes"></a>public (attributs C++)

Garantit qu’un typedef sera placé dans la bibliothèque de types, même s’il n’est pas référencé dans le fichier. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[public]
```

## <a name="remarks"></a>Notes

L' **`public`** attribut C++ a les mêmes fonctionnalités que l’attribut MIDL [public](/windows/win32/Midl/public) .

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l' **`public`** attribut :

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
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
