---
title: call_as (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: 16839f5a5040e6b0019005912782ba359178cc47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579895"
---
# <a name="callas"></a>call_as

Permet une [local](local-cpp.md) fonction être mappée à une fonction à distance afin que lorsque la fonction à distance est appelée, la fonction locale soit appelée.

## <a name="syntax"></a>Syntaxe

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Paramètres

*function*<br/>
La fonction locale que vous souhaitez être appelée lorsqu’une fonction à distance est appelée.

## <a name="remarks"></a>Notes

Le **call_as** attribut C++ a les mêmes fonctionnalités que le [call_as](/windows/desktop/Midl/call-as) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez utiliser **call_as** pour mapper une fonction non accessibles à distance (`f1`) à une fonction accessible à distance (`Remf1`) :

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Aucune|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[local](local-cpp.md)