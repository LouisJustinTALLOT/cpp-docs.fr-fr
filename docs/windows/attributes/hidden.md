---
title: masqué (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 9bfe3858070f4dbbd226d46479609f5d0a630956
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790917"
---
# <a name="hidden"></a>hidden

Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Notes

Le **masqué** attribut C++ a les mêmes fonctionnalités que le [masqué](/windows/desktop/Midl/hidden) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour obtenir un exemple montrant comment utiliser **masqué**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **classe**, **struct**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (lorsqu’il est appliqué à **classe** ou **struct**)|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)  