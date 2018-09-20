---
title: personnalisé (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec3ba8280ab481211d98c9dc5256c94e76e193e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396441"
---
# <a name="custom-c"></a>custom (C++)

Définit les métadonnées pour un objet dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
ID unique.

*valeur*<br/>
Une valeur qui peut être placée dans un variant.

## <a name="remarks"></a>Notes

Le **personnalisé** attribut C++ entraînera des informations d’être placées dans la bibliothèque de types. Vous devez un outil qui lit la valeur personnalisée à partir de la bibliothèque de types.

Le **personnalisé** attribut a les mêmes fonctionnalités que le [personnalisé](/windows/desktop/Midl/custom) attribut MIDL.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Non-COM **interface**, **classe**, **enum**s, `idl_module` méthodes, les membres d’interface, les paramètres de l’interface, **typedef**s, **union**s, **struct**s|
|**Renouvelable**|Oui|
|**Attributs requis**|**coclasse** (lorsqu’il est utilisé pour la classe)|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs autonomes](../windows/stand-alone-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](../windows/parameter-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[Attributs de classe](../windows/class-attributes.md)<br/>
[Attributs d’interface](../windows/interface-attributes.md)  