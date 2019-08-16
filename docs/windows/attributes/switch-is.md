---
title: switch_is (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: b72052f4cbd7f94b170ea58b8f7b284b85d7ab00
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513981"
---
# <a name="switch_is"></a>switch_is

Spécifie l’expression ou l’identificateur agissant comme le discriminante d’Union qui sélectionne le membre Union.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_is]
```

## <a name="remarks"></a>Notes

L’attribut **switch_is** C++ a les mêmes fonctionnalités que l’attribut MIDL [switch_is](/windows/win32/Midl/switch-is) .

## <a name="example"></a>Exemples

Pour obtenir un exemple d’utilisation de **switch_is**, consultez l’exemple de [cas](case-cpp.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)