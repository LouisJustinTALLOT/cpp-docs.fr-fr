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
ms.openlocfilehash: ab7207abac26d85faf27a0ed3d33dadadbdc9d27
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583763"
---
# <a name="requestedit"></a>requestedit

Indique que la propriété prend en charge la `OnRequestEdit` notification.

## <a name="syntax"></a>Syntaxe

```cpp
[requestedit]
```

## <a name="remarks"></a>Notes

Le **requestedit** attribut C++ a les mêmes fonctionnalités que le [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155) attribut MIDL.

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

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de méthode](../windows/method-attributes.md)  
[Attributs de membre de données](../windows/data-member-attributes.md)  
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  