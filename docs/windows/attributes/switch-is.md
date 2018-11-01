---
title: switch_is (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: e70f7d3d7419c25f0c5f9df8006e1d795c8b4361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467287"
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

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)