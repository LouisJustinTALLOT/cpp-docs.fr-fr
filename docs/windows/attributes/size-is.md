---
title: size_is (C++ attribut COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: a7b990a708bafba78c9dc4153315f8b7b20351ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407326"
---
# <a name="sizeis"></a>size_is

Spécifiez la taille de mémoire allouée pour les pointeurs de taille, en taille réelle des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.

## <a name="syntax"></a>Syntaxe

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
La taille de mémoire allouée pour les pointeurs de taille.

## <a name="remarks"></a>Notes

Le **size_is** C++ attribut a les mêmes fonctionnalités que le [size_is](/windows/desktop/Midl/size-is) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [first_is](first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`max_is`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)