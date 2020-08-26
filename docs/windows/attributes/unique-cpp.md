---
title: unique (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: 8b0bd5be19baddaed367bb619135be5cea8e7677
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836154"
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

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`typedef`**, **`struct`** , **`union`** , paramètre d’interface, méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)
