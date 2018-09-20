---
title: helpstringcontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47afe841a2a8e4a1c41baf68dfd139a70b320c7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394463"
---
# <a name="helpstringcontext"></a>helpstringcontext

Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringcontext(
   contextID
) ]
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

[   object,
   helpstring("help string"),
   helpstringcontext(1),
   uuid="11111111-1111-1111-1111-111111111111"
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

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs d’interface](../windows/interface-attributes.md)<br/>
[Attributs de classe](../windows/class-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[module](../windows/module-cpp.md)  