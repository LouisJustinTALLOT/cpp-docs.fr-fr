---
description: 'En savoir plus sur : personnalisé (C++)'
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7771230fd6eed5f567fb2e74e8cd869a0b3618f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333145"
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

- **S’applique à**: non-com `interface` , `idl_module` les méthodes, les membres d’interface, les paramètres d’interface,,,,, **`typedef`** et les **`class`** **`enum`** **`union`** **`struct`** types.
- **Renouvelable**: Oui.
- **Attributs requis**: **coclass** (en cas d’utilisation sur la classe).
- **Attributs non valides**: aucun.

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
