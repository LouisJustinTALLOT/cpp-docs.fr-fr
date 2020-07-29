---
title: AppObject (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: ae3547a32e6d5984a9ef95e495ba119c3a2ed385
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222158"
---
# <a name="appobject"></a>appobject

Identifie la coclasse sous la forme d’un objet d’application, qui est associé à une application. exe complète, et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette [bibliothèque de types](../../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Syntaxe

```cpp
[appobject]
```

## <a name="remarks"></a>Notes

L’attribut C++ **AppObject** a les mêmes fonctionnalités que l’attribut MIDL [AppObject](/windows/win32/Midl/appobject) .

## <a name="example"></a>Exemple

Le code suivant illustre une définition de classe simple précédée d’un bloc d’attributs incluant **AppObject**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|`coclass`|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
