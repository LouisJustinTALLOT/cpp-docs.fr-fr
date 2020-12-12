---
description: 'En savoir plus sur : AppObject'
title: AppObject (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: b371b9726e3a750ef5d40ebe5abae219b473bb02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205458"
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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Renouvelable**|Non|
|**Attributs requis**|`coclass`|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
