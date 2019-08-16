---
title: Export (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501602"
---
# <a name="export"></a>exporter

Entraîne le placement d’une structure de données dans le fichier. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Notes

L’attribut **Export** C++ entraîne le placement d’une structure de données dans le fichier. idl, puis sa disponibilité dans la bibliothèque de types dans un format compatible binaire qui le rend disponible pour une utilisation avec n’importe quel langage.

Vous ne pouvez pas appliquer l’attribut d' **exportation** à une classe, même si la classe n’a que des membres publics (l’équivalent d’un **struct**).

Si vous exportez une **énumération** ou une **structure**sans nom, elle reçoit un nom qui commence par **__unnamed**<em>x</em>, où *x* est un nombre séquentiel.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**Union**, **typedef**, **enum**, **struct**ou **interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)