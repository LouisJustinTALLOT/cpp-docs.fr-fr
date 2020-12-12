---
description: 'En savoir plus sur : defaultvtable'
title: defaultvtable (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 9cabb2e3487788b56a37e7380ef9a9e08cf2bc67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122146"
---
# <a name="defaultvtable"></a>defaultvtable

Définit une interface comme interface vtable par défaut pour un objet COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Paramètres

*interface*<br/>
Interface désignée dont vous souhaitez obtenir la vtable par défaut pour l’objet COM.

## <a name="remarks"></a>Notes

L’attribut C++ **defaultvtable** a les mêmes fonctionnalités que l’attribut MIDL [defaultvtable](/windows/win32/Midl/defaultvtable) .

## <a name="example"></a>Exemple

Le code suivant affiche les attributs d’une classe qui utilisent **defaultvtable** pour spécifier une interface par défaut :

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
