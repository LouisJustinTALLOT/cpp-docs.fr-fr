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
ms.openlocfilehash: 5a491c120dff7f8f505878d6887498eb5f05fb22
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790745"
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

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)  