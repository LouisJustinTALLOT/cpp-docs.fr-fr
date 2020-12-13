---
description: 'En savoir plus sur : valeur par défaut (C++)'
title: default (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 83c4a17f513db755395ed978d57c9c6f01f84ca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333004"
---
# <a name="default-c"></a>default (C++)

Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.

## <a name="syntax"></a>Syntaxe

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Paramètres

*interface1*<br/>
Interface par défaut qui sera mise à la disposition des environnements de script qui créent un objet basé sur la classe définie avec l' **`default`** attribut.

Si aucune interface par défaut n’est spécifiée, la première occurrence d’une interface non source est utilisée par défaut.

*interface2*<br/>
Facultatif Interface source par défaut. Vous devez aussi spécifier cette interface avec l’attribut [source](source-cpp.md) .

Si aucune interface source par défaut n’est spécifiée, la première interface source est utilisée par défaut.

## <a name="remarks"></a>Notes

L' **`default`** attribut C++ a les mêmes fonctionnalités que l’attribut MIDL [par défaut](/windows/win32/Midl/default) . L' **`default`** attribut est également utilisé avec l’attribut [case](case-cpp.md) .

## <a name="example"></a>Exemple

Le code suivant montre comment **`default`** est utilisé sur la définition d’une coclasse pour spécifier `ICustomDispatch` comme interface de programmabilité par défaut :

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

L’attribut [source](source-cpp.md) présente également un exemple d’utilisation de **`default`** .

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`** , données membres|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (quand elle est appliquée à **`class`** ou **`struct`** )|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[coclasse](coclass.md)
