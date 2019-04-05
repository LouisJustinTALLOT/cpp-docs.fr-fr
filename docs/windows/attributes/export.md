---
title: Export (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 5ffa4283b8a2b265809d06b72be96e217cf8bf9f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023605"
---
# <a name="export"></a>exporter

Provoque une structure de données à placer dans le fichier .idl.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Notes

Le **exporter** attribut C++ provoque une structure de données à placer dans le fichier .idl et soit disponible dans la bibliothèque de types dans un format compatible binaire qui le rend disponible pour une utilisation avec n’importe quel langage.

Vous ne pouvez pas appliquer le **exporter** attribut à une classe, même si la classe a uniquement des membres publics (l’équivalent d’un **struct**).

Si vous exportez un sans nom **enum** ou **struct**, elle reçoit un nom qui commence par **__unnamed**<em>x</em>, où *x* est un numéro séquentiel.

Les typedefs valides pour l’exportation sont des types de base, les structures, unions, énumérations, ou tapez les identificateurs.  Consultez [typedef](/windows/desktop/Midl/typedef) pour plus d’informations.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **exporter** attribut :

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
|**S'applique à**|**Union**, **typedef**, **enum**, **struct**, ou **interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)