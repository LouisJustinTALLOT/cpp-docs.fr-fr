---
title: immediatebind (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.immediatebind
dev_langs:
- C++
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb2169adf5bfce3c1a66e382c79b57c8ef53ef04
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790993"
---
# <a name="immediatebind"></a>immediatebind

Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.

## <a name="syntax"></a>Syntaxe

```cpp
[immediatebind]
```

## <a name="remarks"></a>Notes

Le **immediatebind** attribut C++ a les mêmes fonctionnalités que le [immediatebind](/windows/desktop/Midl/immediatebind) attribut MIDL.

## <a name="example"></a>Exemple

Consultez [peut être liée](bindable.md) pour obtenir un exemple montrant comment utiliser **immediatebind**.

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
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)  