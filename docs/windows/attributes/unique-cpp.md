---
title: unique (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: a46d607ef03fcb75fea31835726d0e2d95e71df8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201022"
---
# <a name="unique-c"></a>unique (C++)

Spécifie un pointeur unique.

## <a name="syntax"></a>Syntaxe

```cpp
[unique]
```

## <a name="remarks"></a>Notes

L’attribut C++ **unique** a les mêmes fonctionnalités que l’attribut MIDL [unique](/windows/win32/Midl/unique) .

## <a name="example"></a>Exemple

Consultez l’exemple [ref](ref-cpp.md) pour obtenir un exemple d’utilisation de **unique**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`typedef`**, **`struct`** , **`union`** , paramètre d’interface, méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)
