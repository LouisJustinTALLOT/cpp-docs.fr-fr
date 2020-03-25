---
title: async_uuid (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 537bd6d645532d9d5d20b740125c66f3953239bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168458"
---
# <a name="async_uuid"></a>async_uuid

Spécifie l’UUID qui indique au compilateur MIDL de définir à la fois les versions synchrones et asynchrones d’une interface COM.

## <a name="syntax"></a>Syntaxe

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
UUID qui identifie la version de l’interface.

## <a name="remarks"></a>Notes

L’attribut **async_uuid** C++ a les mêmes fonctionnalités que l’attribut MIDL [async_uuid](/windows/win32/Midl/async-uuid) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|`interface`|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|**Dual**, **dispinterface**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
