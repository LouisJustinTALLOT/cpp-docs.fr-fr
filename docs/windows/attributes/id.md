---
title: ID (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a17edd3ec3c35c307ca35a6657c69f3f7fef246a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790629"
---
# <a name="id"></a>ID

Spécifie un *dispid* paramètre pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Paramètres

*DISPID*<br/>
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

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)  