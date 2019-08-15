---
title: max_is (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: f2e6db997891817620c1b2c1f70cb310818dd346
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514425"
---
# <a name="max_is"></a>max_is

Désigne la valeur maximale d’un index de tableau valide.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Une ou plusieurs expressions en langage C. Les emplacements d’arguments vides sont autorisés.

## <a name="remarks"></a>Notes

L’attribut **max_is** C++ a les mêmes fonctionnalités que l’attribut MIDL [max_is](/windows/win32/Midl/max-is) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ dans un **struct** ou une **Union**, un paramètre d’interface, une méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|**size_is**|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Exemples

Pour obtenir un exemple de spécification d’une section d’un tableau, consultez [first_is](first-is.md) .

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)