---
title: helpstringdll (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 8d6dddef666f074a57f54b8c9447847ff56d26fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501478"
---
# <a name="helpstringdll"></a>helpstringdll

Spécifie le nom de la DLL à utiliser pour effectuer une recherche de chaîne de document (localisation).

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Paramètres

*string*<br/>
DLL à utiliser pour effectuer une recherche de chaîne de document.

## <a name="remarks"></a>Notes

L’attribut **helpstringdll** C++ a les mêmes fonctionnalités que l’attribut MIDL [helpstringdll](/windows/win32/Midl/helpstringdll) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **interface**, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)