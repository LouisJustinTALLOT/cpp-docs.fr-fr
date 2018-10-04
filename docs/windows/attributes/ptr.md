---
title: PTR (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89f00c5e2d65fde2c8a3bb2fd064796c2585c720
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790913"
---
# <a name="ptr"></a>ptr

Désigne un pointeur comme un pointeur complet.

## <a name="syntax"></a>Syntaxe

```cpp
[ptr]
```

## <a name="remarks"></a>Notes

Le **ptr** attribut C++ a les mêmes fonctionnalités que le [ptr](/windows/desktop/Midl/ptr) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](defaultvalue.md) pour un exemple d’utilisation de **ptr**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, la méthode d’interface, **(typedef)**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)  