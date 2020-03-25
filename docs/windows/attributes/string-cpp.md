---
title: String (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 96d5e609130b34a4a5f35109ce691c2de470e537
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166158"
---
# <a name="string-c"></a>string (C++)

Indique que le tableau **char**, **wchar_t**, `byte` (ou équivalent) ou le pointeur vers un tel tableau doit être traité comme une chaîne.

## <a name="syntax"></a>Syntaxe

```cpp
[string]
```

## <a name="remarks"></a>Notes

L’attribut de **chaîne** C++ a les mêmes fonctionnalités que l’attribut MIDL de [chaîne](/windows/win32/Midl/string) .

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
|**S'applique à**|Tableau ou pointeur vers un tableau, un paramètre d’interface, une méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de tableau](array-attributes.md)<br/>
[export](export.md)
