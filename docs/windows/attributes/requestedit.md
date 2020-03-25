---
title: modification (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requestedit
helpviewer_keywords:
- requestedit attribute
ms.assetid: b3c24790-3c4a-4646-8722-03d7b51172ee
ms.openlocfilehash: ec9e516157f2b6ea2a64875f30d2b03412c6eb46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214563"
---
# <a name="requestedit"></a>requestedit

Indique que la propriété prend en charge la notification `OnRequestEdit`.

## <a name="syntax"></a>Syntaxe

```cpp
[requestedit]
```

## <a name="remarks"></a>Notes

L’attribut **modification** C++ a les mêmes fonctionnalités que l’attribut MIDL [modification](/windows/win32/Midl/requestedit) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **modification**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)
