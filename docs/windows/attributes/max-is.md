---
description: 'En savoir plus sur : max_is'
title: max_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: 305acba3a2831448cf677eb16810c567b3561b3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329811"
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

L’attribut C++ **max_is** a les mêmes fonctionnalités que l’attribut MIDL [max_is](/windows/win32/Midl/max-is) .

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Champ dans **`struct`** ou **`union`** , paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|**size_is**|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Exemple

Consultez [first_is](first-is.md) pour obtenir un exemple de spécification d’une section d’un tableau.

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
