---
title: switch_is (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_is
dev_langs:
- C++
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 425caf89619670dd8cabe647b01f8df63be24167
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790688"
---
# <a name="switchis"></a>switch_is

Spécifie l’expression ou l’identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_is]
```

## <a name="remarks"></a>Notes

Le **switch_is** attribut C++ a les mêmes fonctionnalités que le [switch_is](/windows/desktop/Midl/switch-is) attribut MIDL.

## <a name="example"></a>Exemple

Consultez le [cas](case-cpp.md) exemple pour un exemple d’utilisation de **switch_is**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)  