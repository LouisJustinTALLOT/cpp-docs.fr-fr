---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 185517720af7e61f6a04068e8868d258a51f262f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215320"
---
# <a name="custom-c"></a>custom (C++)

Définit les métadonnées d’un objet dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
ID unique.

*value*<br/>
Valeur qui peut être placée dans un variant.

## <a name="remarks"></a>Notes

L’attribut C++ **personnalisé** entraîne la placement des informations dans la bibliothèque de types. Vous aurez besoin d’un outil qui lit la valeur personnalisée à partir de la bibliothèque de types.

L’attribut **personnalisé** a les mêmes fonctionnalités que l’attribut MIDL [personnalisé](/windows/win32/Midl/custom) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**Interface**non com, **`class`** , **`enum`** s, `idl_module` méthodes, membres d’interface, paramètres d’interface, s **`typedef`** **`union`** **`struct`** , s, s|
|**Repeatable Read**|Oui|
|**Attributs requis**|**coclasse** (en cas d’utilisation sur la classe)|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
