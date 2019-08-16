---
title: modification (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requestedit
helpviewer_keywords:
- requestedit attribute
ms.assetid: b3c24790-3c4a-4646-8722-03d7b51172ee
ms.openlocfilehash: e90506619d4f13d4e5627f9c06b997d7034b5f49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514094"
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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)