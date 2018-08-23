---
title: defaultbind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultbind
dev_langs:
- C++
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ec2924fa62370bdc0267cd860a9e2d37c140580
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588921"
---
# <a name="defaultbind"></a>defaultbind

Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
[defaultbind]
```

## <a name="remarks"></a>Notes

Le **defaultbind** attribut C++ a les mêmes fonctionnalités que le [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **defaultbind**.

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

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de méthode](../windows/method-attributes.md)  
[Attributs de membre de données](../windows/data-member-attributes.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  
[requestedit](../windows/requestedit.md)  