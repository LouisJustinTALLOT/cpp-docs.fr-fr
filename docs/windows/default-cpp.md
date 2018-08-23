---
title: par défaut (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe924627b0b0f4f5d02fab0040a4037085d94738
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595581"
---
# <a name="default-c"></a>default (C++)

Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.

## <a name="syntax"></a>Syntaxe

```cpp
[ default(
   interface1,
   interface2
) ]
```

### <a name="parameters"></a>Paramètres

*interface1*  
Interface par défaut qui sera accessible aux environnements de script qui créent un objet en fonction de la classe définie avec l’attribut **default** .

Si aucune interface par défaut n’est spécifiée, la première occurrence d’une interface non source est utilisée par défaut.

*interface2*(facultatif)  
Interface source par défaut. Vous devez aussi spécifier cette interface avec l’attribut [source](../windows/source-cpp.md) .

Si aucune interface source par défaut n’est spécifiée, la première interface source est utilisée par défaut.

## <a name="remarks"></a>Notes

L’attribut C++ **default** a les mêmes fonctionnalités que l’attribut MIDL [default](http://msdn.microsoft.com/library/windows/desktop/aa366787) . L’attribut **default** est aussi utilisé avec l’attribut [case](../windows/case-cpp.md) .

## <a name="example"></a>Exemple

Le code suivant montre comment **par défaut** est utilisé dans la définition d’une coclasse pour spécifier `ICustomDispatch` en tant que l’interface de programmabilité par défaut :

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

[   coclass,
   default(ICustomDispatch),
   source(IDual),
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
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

Il existe aussi un exemple pour l’attribut [source](../windows/source-cpp.md) qui montre comment utiliser **default**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**, membre de données|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (lorsqu’il est appliqué à **classe** ou **struct**)|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de classe](../windows/class-attributes.md)  
[coclass](../windows/coclass.md)  