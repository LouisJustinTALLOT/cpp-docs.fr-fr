---
title: pointer_default (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: d0c5832623c1e418f4c6e8bdb606d1d363503483
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166534"
---
# <a name="pointer_default"></a>pointer_default

Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur qui décrit le type de pointeur : **ptr**, **ref**ou **unique**.

## <a name="remarks"></a>Notes

L’attribut **pointer_default** C++ a les mêmes fonctionnalités que l’attribut MIDL [pointer_default](/windows/win32/Midl/pointer-default) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **pointer_default**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
