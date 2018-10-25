---
title: max_is (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0dc76d9478a2639103196b33c0132c07be76860
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073979"
---
# <a name="maxis"></a>max_is

Désigne la valeur maximale pour un index de tableau valide.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*Expression*<br/>
Une ou plusieurs expressions de langage C. Emplacements d’arguments vide sont autorisés.

## <a name="remarks"></a>Notes

Le **max_is** attribut C++ a les mêmes fonctionnalités que le [max_is](/windows/desktop/Midl/max-is) attribut MIDL.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|**size_is**|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Exemple

Consultez [first_is](first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)