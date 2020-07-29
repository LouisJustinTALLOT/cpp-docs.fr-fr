---
title: source (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 274e446aecc4d0d7096211bbae88e0f170ae44a2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213825"
---
# <a name="source-c"></a>source (C++)

Sur une classe, spécifie les interfaces sources de l’objet COM pour les points de connexion. Sur une propriété ou une méthode, indique que le membre retourne un objet ou une variante qui est une source d’événements.

## <a name="syntax"></a>Syntaxe

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Paramètres

*interfaces*<br/>
Une ou plusieurs interfaces que vous spécifiez lorsque vous appliquez l’attribut source à une classe. Ce paramètre n’est pas utilisé lorsque la source est appliquée à une propriété ou à une méthode.

## <a name="remarks"></a>Notes

L’attribut C++ **source** a les mêmes fonctionnalités que l’attribut MIDL [source](/windows/win32/Midl/source) .

Vous pouvez utiliser l’attribut [default](default-cpp.md) pour spécifier l’interface source par défaut d’un objet.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`class`**, **`struct`** , **interface**|
|**Repeatable Read**|Non|
|**Attributs requis**|`coclass`(en cas d’application à une classe ou à un struct)|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[coclasse](coclass.md)
