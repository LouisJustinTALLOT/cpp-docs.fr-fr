---
description: 'En savoir plus sur : switch_is'
title: switch_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: 88489a9722e79da6629dfc2b39bfbe7f6ab39932
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329566"
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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`typedef`**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)
