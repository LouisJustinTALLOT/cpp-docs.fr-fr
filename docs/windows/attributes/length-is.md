---
title: length_is (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 4f4bfe233e3228c50aee734de4ad979c38a55fda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514527"
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

L’attribut **length_is** C++ a les mêmes fonctionnalités que l’attribut MIDL [length_is](/windows/win32/Midl/length-is) .

## <a name="example"></a>Exemple

Pour obtenir un exemple de spécification d’une section d’un tableau, consultez [first_is](first-is.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ dans un **struct** ou une **Union**, un paramètre d’interface, une méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)