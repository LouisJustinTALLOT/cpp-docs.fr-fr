---
title: helpstringdll (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 17e70a54024b8e5a3ab29e2420f60fbf3eec08a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677238"
---
# <a name="helpstringdll"></a>helpstringdll

Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Paramètres

*string*<br/>
La DLL à utiliser pour effectuer la recherche de chaîne de document.

## <a name="remarks"></a>Notes

Le **helpstringdll** attribut C++ a les mêmes fonctionnalités que le [helpstringdll](/windows/desktop/Midl/helpstringdll) attribut MIDL.

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
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)