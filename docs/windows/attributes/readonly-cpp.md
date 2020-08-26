---
title: ReadOnly (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: ea2b0a46d34fc415a3b9eca97b92cda764fc7d42
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839801"
---
# <a name="readonly-c"></a>readonly (C++)

Interdit l’assignation à un membre de données.

## <a name="syntax"></a>Syntaxe

```cpp
[readonly]
```

## <a name="remarks"></a>Notes

L’attribut C++ **readonly** a les mêmes fonctionnalités que l’attribut MIDL [readonly](/windows/win32/Midl/readonly) .

Si vous souhaitez interdire la modification d’un paramètre de méthode, utilisez l’attribut [in](in-cpp.md) .

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de l’attribut **readonly** :

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)
