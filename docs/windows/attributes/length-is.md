---
description: 'En savoir plus sur : length_is'
title: length_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: b3f913819b88958f294aee42f4cbda07827fa990
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329844"
---
# <a name="length_is"></a>length_is

Spécifie le nombre d’éléments de tableau à transmettre.

## <a name="syntax"></a>Syntaxe

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Une ou plusieurs expressions en langage C. Les emplacements d’arguments vides sont autorisés.

## <a name="remarks"></a>Notes

L’attribut C++ **length_is** a les mêmes fonctionnalités que l’attribut MIDL [length_is](/windows/win32/Midl/length-is) .

## <a name="example"></a>Exemple

Consultez [first_is](first-is.md) pour obtenir un exemple de spécification d’une section d’un tableau.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Champ dans **`struct`** ou **`union`** , paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)
