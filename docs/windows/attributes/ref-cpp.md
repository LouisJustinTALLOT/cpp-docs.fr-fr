---
title: ref (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ref
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
ms.openlocfilehash: c22d04f7a799ea720fb7d69ffc1aa21ddf9db55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468430"
---
# <a name="ref-c"></a>ref (C++)

Identifie un pointeur de référence.

## <a name="syntax"></a>Syntaxe

```cpp
[ref]
```

## <a name="remarks"></a>Notes

Le **ref** attribut C++ a les mêmes fonctionnalités que le [ref](/windows/desktop/Midl/ref) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **ref** attribut :

```cpp
// cpp_attr_ref_ref.cpp
// compile with: /LD
#include <windows.h>
[module(name="ATLFIRELib")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)