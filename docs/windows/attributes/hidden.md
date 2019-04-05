---
title: (C++ COM attribut masqué)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: d1d87ea057b22984a0e0f8f5518899e36f7d0221
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038419"
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

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d'interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)