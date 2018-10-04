---
title: async_uuid (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.async_uuid
dev_langs:
- C++
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 336bbf00edc84335972171aba0e7fc01e206984e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790704"
---
# <a name="asyncuuid"></a>async_uuid

Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.

## <a name="syntax"></a>Syntaxe

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
UUID qui identifie la version de l’interface.

## <a name="remarks"></a>Notes

Le **async_uuid** attribut C++ a les mêmes fonctionnalités que le [async_uuid](/windows/desktop/Midl/async-uuid) attribut MIDL.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|`interface`|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|**Double**, **dispinterface**|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)  