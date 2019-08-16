---
title: Restricted (C++ attribut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 01dabcd15eb1a14734c16b9e54c0ab2e030d0479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514064"
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

L’attribut **Restricted** C++ a les mêmes fonctionnalités que l’attribut MIDL [restreint](/windows/win32/Midl/restricted) .

## <a name="example"></a>Exemples

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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface, **interface**, **classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (en cas d’application à une **classe** ou à un **struct**)|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)