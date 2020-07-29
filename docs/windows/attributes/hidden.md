---
title: Hidden (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: e0e3c5cb0355f3bedd8ecee57b034f0d9dde87df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224433"
---
# <a name="hidden"></a>hidden

Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Notes

L’attribut C++ **masqué** a les mêmes fonctionnalités que l’attribut MIDL [masqué](/windows/win32/Midl/hidden) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **Hidden**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**interface**, **`class`** , **`struct`** , méthode, propriété|
|**Repeatable Read**|Non|
|**Attributs requis**|**coclasse** (quand elle est appliquée à **`class`** ou **`struct`** )|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
