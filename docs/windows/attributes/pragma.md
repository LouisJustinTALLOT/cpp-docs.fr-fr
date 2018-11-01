---
title: pragma (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: d90e37e27f7e2a13ffebd11043e415c1d43751c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430497"
---
# <a name="pragma"></a>pragma

Émet la chaîne spécifiée dans le fichier .idl généré sans utiliser de guillemets.

## <a name="syntax"></a>Syntaxe

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Paramètres

*pragma_statement*<br/>
Le pragma que vous souhaitez aller dans le fichier .idl généré.

## <a name="remarks"></a>Notes

Le **pragma** attribut C++ a les mêmes fonctionnalités que le [pragma](/windows/desktop/Midl/pragma) attribut MIDL.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)