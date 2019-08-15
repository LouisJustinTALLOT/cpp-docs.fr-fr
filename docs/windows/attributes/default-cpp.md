---
title: valeur parC++ défaut (attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 291e16ad0967acd1869874fcc9fa6eb5529e4b44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501683"
---
# <a name="default-c"></a>default (C++)

Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.

## <a name="syntax"></a>Syntaxe

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Paramètres

*interface1*<br/>
Interface par défaut qui sera accessible aux environnements de script qui créent un objet en fonction de la classe définie avec l’attribut **default** .

Si aucune interface par défaut n’est spécifiée, la première occurrence d’une interface non source est utilisée par défaut.

*interface2*<br/>
Facultatif Interface source par défaut. Vous devez aussi spécifier cette interface avec l’attribut [source](source-cpp.md) .

Si aucune interface source par défaut n’est spécifiée, la première interface source est utilisée par défaut.

## <a name="remarks"></a>Notes

L’attribut C++ **default** a les mêmes fonctionnalités que l’attribut MIDL [default](/windows/win32/Midl/default) . L’attribut **default** est aussi utilisé avec l’attribut [case](case-cpp.md) .

## <a name="example"></a>Exemple

Le code suivant montre comment la **valeur par défaut** est utilisée sur la définition d’une coclasse pour spécifier `ICustomDispatch` comme interface de programmabilité par défaut:

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

Il existe aussi un exemple pour l’attribut [source](source-cpp.md) qui montre comment utiliser **default**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**, données membres|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (en cas d’application à une **classe** ou à un **struct**)|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[coclasse](coclass.md)