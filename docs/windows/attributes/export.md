---
title: Export (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 4854789d9f977b3b747fd9b546cb92642942be88
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845274"
---
# <a name="export"></a>export

Entraîne le placement d’une structure de données dans le fichier. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Notes

L' **`[export]`** attribut C++ entraîne le placement d’une structure de données dans le fichier. idl, puis sa disponibilité dans la bibliothèque de types dans un format compatible binaire qui le rend disponible pour une utilisation avec n’importe quel langage.

Vous ne pouvez pas appliquer l' **`[export]`** attribut à une classe même si la classe n’a que des membres publics (l’équivalent d’un **`struct`** ).

Si vous exportez un sans **`enum`** nom ou **`struct`** , il reçoit un nom qui commence par **__unnamed**<em>x</em>, où *x* est un nombre séquentiel.

Les typedefs valides pour l’exportation sont des types de base, des structs, des unions, des enums ou des identificateurs de type.  [`typedef`](/windows/win32/Midl/typedef)Pour plus d’informations, consultez.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l' **`[export]`** attribut :

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`union`**, **`typedef`** , **`enum`** , **`struct`** ou **`interface`**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
