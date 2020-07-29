---
title: String (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 68708cce2e167c6f40b461d52861fe4ed82be867
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213812"
---
# <a name="string-c"></a>string (C++)

Indique que le tableau unidimensionnel **`char`** , **`wchar_t`** , `byte` (ou équivalent) ou le pointeur vers ce tableau doit être traité comme une chaîne.

## <a name="syntax"></a>Syntaxe

```cpp
[string]
```

## <a name="remarks"></a>Notes

L’attribut C++ de **chaîne** a les mêmes fonctionnalités que l’attribut MIDL de [chaîne](/windows/win32/Midl/string) .

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser **String** sur une interface et sur un typedef :

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|Tableau ou pointeur vers un tableau, un paramètre d’interface, une méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de tableau](array-attributes.md)<br/>
[exporter](export.md)
