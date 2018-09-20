---
title: max_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8a66a849dceb5ba28eb6630b513a121e219a3588
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432955"
---
# <a name="maxis"></a>max_is

Désigne la valeur maximale pour un index de tableau valide.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is(
   "expression"
) ]
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

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="example"></a>Exemple

Consultez [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](../windows/parameter-attributes.md)<br/>
[first_is](../windows/first-is.md)<br/>
[last_is](../windows/last-is.md)<br/>
[length_is](../windows/length-is.md)<br/>
[size_is](../windows/size-is.md)  