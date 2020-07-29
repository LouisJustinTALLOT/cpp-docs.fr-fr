---
title: switch_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: 85ee066a12d4297d9a782ae07ef0fa16798f1616
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228048"
---
# <a name="switch_is"></a>switch_is

Spécifie l’expression ou l’identificateur agissant comme le discriminante d’Union qui sélectionne le membre Union.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_is]
```

## <a name="remarks"></a>Notes

L’attribut C++ **switch_is** a les mêmes fonctionnalités que l’attribut MIDL [switch_is](/windows/win32/Midl/switch-is) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **switch_is**, consultez l’exemple de [cas](case-cpp.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`typedef`**|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)
