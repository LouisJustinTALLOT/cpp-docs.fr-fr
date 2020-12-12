---
description: 'En savoir plus sur : ID'
title: ID (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 04f7144e1c6f8b6655b0b6be23e0ffa4f22dc27c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180199"
---
# <a name="id"></a>id

Spécifie un paramètre *DISPID* pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).

## <a name="syntax"></a>Syntaxe

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de la méthode d’interface.

## <a name="remarks"></a>Notes

L’attribut **ID** C++ a les mêmes fonctionnalités que l’attribut MIDL [ID](/windows/win32/Midl/id) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **ID**, consultez l’exemple de [Bindable](bindable.md) .

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[DefaultValue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[à](out-cpp.md)
