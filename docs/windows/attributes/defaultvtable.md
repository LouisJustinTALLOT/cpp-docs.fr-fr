---
title: defaultvtable (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 6b1d6960a065bf2df46852d3df1ca53d4239f1bc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839489"
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

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
