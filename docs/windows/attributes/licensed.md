---
title: sous licenceC++ (attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.licensed
helpviewer_keywords:
- licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
ms.openlocfilehash: 0c637f9e3f6d99b9f197474f49a1a9843744f38b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514456"
---
# <a name="licensed"></a>licensed

Indique que l’objet COM auquel il s’applique est concédé sous licence et doit être instancié à `IClassFactory2`l’aide de.

## <a name="syntax"></a>Syntaxe

```cpp
[licensed]
```

## <a name="remarks"></a>Notes

L’attribut **sous licence** C++ a les mêmes fonctionnalités que l’attribut MIDL [sous licence](/windows/win32/Midl/licensed) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_licensed.cpp
// compile with: /LD
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {
   HRESULT f();
};

[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),
licensed, threading(free), progid(some.name)]
class CSample : public IMyI {
public:
   int nSize;
};

[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|`coclass`|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)