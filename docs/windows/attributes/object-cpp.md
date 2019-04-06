---
title: objet (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022357"
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
[Attributs d'interface](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[personnalisé](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)