---
title: pointer_default (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: e4e5ce03e8c0e6ca19814f5d228305b0d97322f9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836190"
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

L’attribut C++ **pointer_default** a les mêmes fonctionnalités que l’attribut MIDL [pointer_default](/windows/win32/Midl/pointer-default) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **pointer_default**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
