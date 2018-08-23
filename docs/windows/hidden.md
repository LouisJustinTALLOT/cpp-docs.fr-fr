---
title: masqué | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9523fc63e36d9a2b93dc6df1a49627ac5fbebc9b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602153"
---
# <a name="hidden"></a>hidden

Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Notes

Le **masqué** attribut C++ a les mêmes fonctionnalités que le [masqué](http://msdn.microsoft.com/library/windows/desktop/aa366861) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour obtenir un exemple montrant comment utiliser **masqué**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **classe**, **struct**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (lorsqu’il est appliqué à **classe** ou **struct**)|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs d’interface](../windows/interface-attributes.md)  
[Attributs de classe](../windows/class-attributes.md)  
[Attributs de méthode](../windows/method-attributes.md)  