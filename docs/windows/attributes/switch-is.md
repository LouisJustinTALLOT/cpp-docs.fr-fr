---
title: switch_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: b017ba6dd2bbdfab7bfb5fa2dbf19e613e14772b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840535"
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

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`typedef`**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)
