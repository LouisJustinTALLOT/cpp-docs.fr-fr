---
title: size_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0505fde4ea92c643a6038d64d10ec06cda9cb60d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392331"
---
# <a name="sizeis"></a>size_is

Spécifiez la taille de mémoire allouée pour les pointeurs de taille, en taille réelle des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.

## <a name="syntax"></a>Syntaxe

```cpp
[ size_is(
   "expression"
) ]
```

### <a name="parameters"></a>Paramètres

*Expression*<br/>
La taille de mémoire allouée pour les pointeurs de taille.

## <a name="remarks"></a>Notes

Le **size_is** attribut C++ a les mêmes fonctionnalités que le [size_is](/windows/desktop/Midl/size-is) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`max_is`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](../windows/parameter-attributes.md)<br/>
[first_is](../windows/first-is.md)<br/>
[last_is](../windows/last-is.md)<br/>
[max_is](../windows/max-is.md)<br/>
[length_is](../windows/length-is.md)  