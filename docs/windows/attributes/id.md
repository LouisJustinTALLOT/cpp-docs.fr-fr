---
title: ID (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501406"
---
# <a name="id"></a>id

Spécifie un paramètre *DISPID* pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
ID de dispatch de la méthode d’interface.

## <a name="remarks"></a>Notes

L’attribut **ID** C++ a les mêmes fonctionnalités que l’attribut MIDL [ID](/windows/win32/Midl/id) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **ID**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)