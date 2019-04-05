---
title: ID (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 5faf08418771deda3086a434cff6b1900a37e36e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034694"
---
# <a name="id"></a>ID

Spécifie un *dispid* paramètre pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’ID de dispatch pour la méthode d’interface.

## <a name="remarks"></a>Notes

Le **id** attribut C++ a les mêmes fonctionnalités que le [id](/windows/desktop/Midl/id) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour obtenir un exemple montrant comment utiliser **id**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[dans](in-cpp.md)<br/>
[out](out-cpp.md)