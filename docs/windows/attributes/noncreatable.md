---
title: noncreatable (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: acfb5ea65e4efcba13d6b376dbb2d0f2fe3e6855
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067863"
---
# <a name="noncreatable"></a>noncreatable

Définit un objet qui ne peut pas être instancié par lui-même.

## <a name="syntax"></a>Syntaxe

```cpp
[noncreatable]
```

## <a name="remarks"></a>Notes

Le **noncreatable** attribut C++ a les mêmes fonctionnalités que le [noncreatable](/windows/desktop/Midl/noncreatable) attribut MIDL et est automatiquement transféré vers le texte généré. Fichier IDL par le compilateur.

Lorsque cet attribut est utilisé au sein d’un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit ci-dessus, l’attribut injecte également le [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro. Cette macro indique à ATL que l’objet ne peut pas être créé en externe.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
