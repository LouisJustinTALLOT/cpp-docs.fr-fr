---
title: immediatebind (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 1844e72ecd1fe7c0f4255426eb48f5c70471e5f5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036206"
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

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)