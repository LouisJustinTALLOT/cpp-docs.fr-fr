---
title: displaybind (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.displaybind
helpviewer_keywords:
- displaybind attribute
ms.assetid: b3d70396-78e4-43d9-9583-16ddb8c9bb1f
ms.openlocfilehash: 42eedf5d67de71860ecfe5f224914b80f3674a43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493754"
---
# <a name="displaybind"></a>displaybind

Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.

## <a name="syntax"></a>Syntaxe

```cpp
[displaybind]
```

## <a name="remarks"></a>Notes

Le **displaybind** attribut C++ a les mêmes fonctionnalités que le [displaybind](/windows/desktop/Midl/displaybind) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour obtenir un exemple montrant comment utiliser **displaybind**.

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
[defaultbind](defaultbind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)