---
title: objet (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 1cae9e6b014f33dfbbcccdeb4172d6f35349e307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526160"
---
# <a name="object-c"></a>object (C++)

Identifie une interface personnalisée.

## <a name="syntax"></a>Syntaxe

```cpp
[object]
```

## <a name="remarks"></a>Notes

Lorsqu’il précède une définition d’interface, le **objet** attribut C++ provoque l’interface à placer dans le fichier .idl comme une interface personnalisée.

N’importe quelle interface marquée avec l’objet doit hériter `IUnknown`. Cette condition est remplie si une des interfaces de base héritent `IUnknown`. Si aucune interface de base ne hérite `IUnknown`, le compilateur entraîne l’interface marquée avec **objet** de dériver de `IUnknown`.

## <a name="example"></a>Exemple

Consultez [nonbrowsable](nonbrowsable.md) pour obtenir un exemple montrant comment utiliser **objet**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)