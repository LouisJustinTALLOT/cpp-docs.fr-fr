---
title: noncreatable (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: c5d51d7c5628a875f036b4e48b03b317490b37ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224394"
---
# <a name="noncreatable"></a>noncreatable

Définit un objet qui ne peut pas être instancié par lui-même.

## <a name="syntax"></a>Syntaxe

```cpp
[noncreatable]
```

## <a name="remarks"></a>Notes

L’attribut C++ non **pouvant être créé** a les mêmes fonctionnalités que l’attribut MIDL [pouvant être créé](/windows/win32/Midl/noncreatable) et est transmis automatiquement au généré. Fichier IDL par le compilateur.

Lorsque cet attribut est utilisé dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement ci-dessus, l’attribut injecte également la macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) . Cette macro indique à ATL que l’objet ne peut pas être créé en externe.

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

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
