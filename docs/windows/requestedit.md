---
title: requestedit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requestedit
dev_langs:
- C++
helpviewer_keywords:
- requestedit attribute
ms.assetid: b3c24790-3c4a-4646-8722-03d7b51172ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5555a71ae9bbe8daf0de9361a01d11431574e574
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422361"
---
# <a name="requestedit"></a>requestedit

Indique que la propriété prend en charge la `OnRequestEdit` notification.

## <a name="syntax"></a>Syntaxe

```cpp
[requestedit]
```

## <a name="remarks"></a>Notes

Le **requestedit** attribut C++ a les mêmes fonctionnalités que le [requestedit](/windows/desktop/Midl/requestedit) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **requestedit**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[Attributs de membre de données](../windows/data-member-attributes.md)<br/>
[defaultbind](../windows/defaultbind.md)<br/>
[displaybind](../windows/displaybind.md)<br/>
[immediatebind](../windows/immediatebind.md)  