---
title: Object (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0c0ff552d8a33ebe70f56b9b186e963cc8e9b3d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843103"
---
# <a name="object-c"></a>object (C++)

Identifie une interface personnalisée.

## <a name="syntax"></a>Syntaxe

```cpp
[object]
```

## <a name="remarks"></a>Notes

En cas de préfixe d’une définition d’interface, l’attribut C++ de l' **objet** provoque le placement de l’interface dans le fichier. idl en tant qu’interface personnalisée.

Toute interface marquée avec l’objet doit hériter de `IUnknown` . Cette condition est satisfaite si l’une des interfaces de base hérite de `IUnknown` . Si aucune interface de base n’hérite de `IUnknown` , le compilateur fera en sorte que l’interface marquée avec l' **objet** dérive de `IUnknown` .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **objet**, consultez non [consultable](nonbrowsable.md) .

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[propre](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
