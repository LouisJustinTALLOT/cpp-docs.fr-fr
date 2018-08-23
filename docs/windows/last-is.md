---
title: last_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b09b6c89a6dccd0b1cc78346838b79aacb7e9200
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594549"
---
# <a name="lastis"></a>last_is

Spécifie l’index du dernier élément de tableau doit être transmis.

## <a name="syntax"></a>Syntaxe

```cpp
[ last_is(
   "expression"
) ]
```

### <a name="parameters"></a>Paramètres

*Expression*  
Une ou plusieurs expressions de langage C. Emplacements d’arguments vide sont autorisés.

## <a name="remarks"></a>Notes

Le **last_is** attribut C++ a les mêmes fonctionnalités que le [last_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) attribut MIDL.

## <a name="example"></a>Exemple

Consultez [first_is](../windows/first-is.md) pour obtenir un exemple montrant comment spécifier une section d’un tableau.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Champ **struct** ou **union**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Attributs de paramètres](../windows/parameter-attributes.md)  
[first_is](../windows/first-is.md)  
[max_is](../windows/max-is.md)  
[length_is](../windows/length-is.md)  
[size_is](../windows/size-is.md)  