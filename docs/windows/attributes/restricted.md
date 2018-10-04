---
title: restreint (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1dfaed296242d2a0fc341c2ff5f137a08d753e71
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790653"
---
# <a name="restricted"></a>restricted

Spécifie qu’un membre d’un module, une interface ou une dispinterface ne peut pas être appelé arbitrairement.

## <a name="syntax"></a>Syntaxe

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Paramètres

*interfaces*<br/>
Une ou plusieurs interfaces qui ne peuvent pas être appelées arbitrairement sur un objet COM. Ce paramètre est uniquement valide lorsqu’il est appliqué à une classe.

## <a name="remarks"></a>Notes

Le **restreint** attribut C++ a les mêmes fonctionnalités que le [restreint](/windows/desktop/Midl/restricted) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **restreint** attribut :

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
|**S'applique à**|Méthode, d’interface **interface**, **classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** (lorsqu’il est appliqué à **classe** ou **struct**)|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)  