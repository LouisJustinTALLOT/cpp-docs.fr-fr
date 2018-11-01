---
title: helpstringcontext (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: d292dd53ff3009a571dd5b0a1ba102e75b648e4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533599"
---
# <a name="helpstringcontext"></a>helpstringcontext

Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Paramètres

*contextID*<br/>
Un identificateur de contexte d’aide 32 bits dans le **aide** fichier.

## <a name="remarks"></a>Notes

Le **helpstringcontext** attribut C++ a les mêmes fonctionnalités que le [helpstringcontext](/windows/desktop/Midl/helpstringcontext) ODL (attribut).

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **interface**, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[module](module-cpp.md)