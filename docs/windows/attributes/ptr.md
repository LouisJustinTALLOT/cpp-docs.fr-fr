---
title: PTR (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: 9e45cd529562fe238f96f98cf7f91e15df34270a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224381"
---
# <a name="ptr"></a>ptr

Désigne un pointeur comme un pointeur complet.

## <a name="syntax"></a>Syntaxe

```cpp
[ptr]
```

## <a name="remarks"></a>Notes

L’attribut C++ **ptr** a les mêmes fonctionnalités que l’attribut MIDL [ptr](/windows/win32/Midl/ptr) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **ptr**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|Paramètre d’interface, méthode d’interface,**`typedef`**|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
