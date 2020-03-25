---
title: pragma (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 56b1aa4bf445095b86a1ea6792bfc78f45266e9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166482"
---
# <a name="pragma"></a>pragma

Émet la chaîne spécifiée dans le fichier. idl généré sans utiliser de guillemets.

## <a name="syntax"></a>Syntaxe

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Paramètres

*pragma_statement*<br/>
Le pragma que vous souhaitez placer dans le fichier. idl généré.

## <a name="remarks"></a>Notes

L’attribut **pragma** C++ a les mêmes fonctionnalités que l’attribut MIDL [pragma](/windows/win32/Midl/pragma) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)
