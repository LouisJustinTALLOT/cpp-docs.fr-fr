---
title: ID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 13ddef5b6bb83de16c72438e2b9f2bb3d4e8d635
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386351"
---
# <a name="id"></a>ID

Spécifie un *dispid* paramètre pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(
   dispid
) ]
```

### <a name="parameters"></a>Paramètres

*DISPID*<br/>
L’ID de dispatch pour la méthode d’interface.

## <a name="remarks"></a>Notes

Le **id** attribut C++ a les mêmes fonctionnalités que le [id](/windows/desktop/Midl/id) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **id**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[Attributs de membre de données](../windows/data-member-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[in](../windows/in-cpp.md)<br/>
[out](../windows/out-cpp.md)  