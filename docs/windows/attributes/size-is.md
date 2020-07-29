---
title: size_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 36b960982d1f88cd30bab707dfe7aec73381dfab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213838"
---
# <a name="size_is"></a>size_is

Spécifiez la taille de la mémoire allouée aux pointeurs dimensionnés, aux pointeurs dimensionnés aux pointeurs dimensionnés et aux tableaux à une ou plusieurs dimensions.

## <a name="syntax"></a>Syntaxe

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Taille de la mémoire allouée pour les pointeurs de taille.

## <a name="remarks"></a>Notes

L’attribut C++ **size_is** a les mêmes fonctionnalités que l’attribut MIDL [size_is](/windows/win32/Midl/size-is) .

## <a name="example"></a>Exemple

Consultez l’exemple de [first_is](first-is.md) pour obtenir un exemple de spécification d’une section d’un tableau.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|Champ dans **`struct`** ou **`union`** , paramètre d’interface, méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`max_is`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)
