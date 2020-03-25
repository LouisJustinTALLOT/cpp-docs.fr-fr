---
title: Export (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 6264db037069f5fc6b858bdd466ce6c68b814a84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167042"
---
# <a name="export"></a>export

Entraîne le placement d’une structure de données dans le fichier. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Notes

L’attribut **Export** C++ entraîne le placement d’une structure de données dans le fichier. idl, puis sa disponibilité dans la bibliothèque de types dans un format compatible binaire qui le rend disponible pour une utilisation avec n’importe quel langage.

Vous ne pouvez pas appliquer l’attribut d' **exportation** à une classe, même si la classe n’a que des membres publics (l’équivalent d’un **struct**).

Si vous exportez un **enum** ou un **struct**sans nom, un nom commençant par **__unnamed**<em>x</em>est attribué, où *x* est un nombre séquentiel.

Les typedefs valides pour l’exportation sont des types de base, des structs, des unions, des enums ou des identificateurs de type.  Pour plus d’informations, consultez [typedef](/windows/win32/Midl/typedef) .

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l’attribut **Export** :

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**Union**, **typedef**, **enum**, **struct**ou **interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)
