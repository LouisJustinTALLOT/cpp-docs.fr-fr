---
title: defaultbind (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultbind
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
ms.openlocfilehash: 36225dae3dffbd57d291989c56ac2995278a1bee
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842401"
---
# <a name="defaultbind"></a>defaultbind

Indique la propriété unique pouvant être liée qui représente le mieux l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
[defaultbind]
```

## <a name="remarks"></a>Notes

L’attribut C++ **defaultbind** a les mêmes fonctionnalités que l’attribut MIDL [defaultbind](/windows/win32/Midl/defaultbind) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **defaultbind**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)
