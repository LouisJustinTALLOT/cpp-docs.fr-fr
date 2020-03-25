---
title: ID (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 79e49b2c074cd82323c74489e33812c10c442c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168055"
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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)
