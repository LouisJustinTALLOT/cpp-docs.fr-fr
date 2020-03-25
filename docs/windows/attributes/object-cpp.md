---
title: Object (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214663"
---
# <a name="object-c"></a>object (C++)

Identifie une interface personnalisée.

## <a name="syntax"></a>Syntaxe

```cpp
[object]
```

## <a name="remarks"></a>Notes

Lors de la préversion d’une définition d’interface, l’attribut de l' **objet** C++ provoque le placement de l’interface dans le fichier. idl en tant qu’interface personnalisée.

Toute interface marquée avec l’objet doit hériter de `IUnknown`. Cette condition est satisfaite si l’une des interfaces de base hérite de `IUnknown`. Si aucune interface de base n’hérite de `IUnknown`, le compilateur fait en sorte que l’interface marquée avec l' **objet** soit dérivée de `IUnknown`.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **objet**, consultez non [consultable](nonbrowsable.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
