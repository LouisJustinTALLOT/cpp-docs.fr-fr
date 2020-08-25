---
title: ms_union (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ms_union
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
ms.openlocfilehash: ae99a996cd7969da27f38ad3532f0472f389ee3d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838839"
---
# <a name="ms_union"></a>ms_union

Contrôle l’alignement de la représentation des données réseau des unions qui ne sont pas encapsulées.

## <a name="syntax"></a>Syntaxe

```cpp
[ms_union]
```

## <a name="remarks"></a>Notes

L’attribut C++ **ms_union** a les mêmes fonctionnalités que l’attribut MIDL [ms_union](/windows/win32/Midl/ms-union-attrib) .

## <a name="example"></a>Exemple

Le code suivant illustre l’emplacement des **ms_union**:

```cpp
// cpp_attr_ref_ms_union.cpp
// compile with: /LD
#include <unknwn.h>
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl {
   HRESULT DisplayString([in, string] char * p1);
};

[export, switch_type(short)] union _WILLIE_UNION_TYPE  {
   [case(24)]
      float fMays;
   [case(25)]
      double dMcCovey;
   [default]
      int x;
};

[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Unions qui ne sont pas encapsulées|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`dispinterface`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
