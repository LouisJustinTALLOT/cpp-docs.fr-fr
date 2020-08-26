---
title: Restricted (attribut COM C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: a1f543c4d8edac751195d37414c030dfe2df94fa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846353"
---
# <a name="restricted"></a>restricted

Spécifie qu’un membre d’un module, d’une interface ou d’une dispinterface ne peut pas être appelé arbitrairement.

## <a name="syntax"></a>Syntaxe

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Paramètres

*interfaces*<br/>
Une ou plusieurs interfaces qui ne peuvent pas être appelées arbitrairement sur un objet COM. Ce paramètre est valide uniquement lorsqu’il est appliqué à une classe.

## <a name="remarks"></a>Notes

L’attribut C++ **restreint** a les mêmes fonctionnalités que l’attribut MIDL [restreint](/windows/win32/Midl/restricted) .

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l’attribut **Restricted** :

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface, **interface**, **`class`** , **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|**coclasse** (quand elle est appliquée à **`class`** ou **`struct`** )|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
