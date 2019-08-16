---
title: Hidden (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501446"
---
# <a name="hidden"></a>hidden

Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Notes

L’attribut **Hidden** C++ a les mêmes fonctionnalités que l’attribut MIDL [masqué](/windows/win32/Midl/hidden) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **Hidden**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **classe**, **struct**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (en cas d’application à une **classe** ou à un **struct**)|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)