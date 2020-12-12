---
description: 'En savoir plus sur : helpstringdll'
title: helpstringdll (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 13a64f7f98a9d63e6a176911caad1246ad64af75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148796"
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

L’attribut C++ **helpstringdll** a les mêmes fonctionnalités que l’attribut MIDL [helpstringdll](/windows/win32/Midl/helpstringdll) .

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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **interface**, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
