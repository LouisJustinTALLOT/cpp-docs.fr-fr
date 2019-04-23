---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 227e67696e679452a9c6c0e18c04e3d918f7a93f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029432"
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

*value*<br/>
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

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)