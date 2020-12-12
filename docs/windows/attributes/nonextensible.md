---
description: 'En savoir plus sur : pas extensible'
title: unextensible (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: dfb0eda0fc8c6de367ee29ec3786750ba40395ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327448"
---
# <a name="nonextensible"></a>nonextensible

Spécifie que l' `IDispatch` implémentation de comprend uniquement les propriétés et les méthodes listées dans la description de l’interface et ne peut pas être étendue avec des membres supplémentaires au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Notes

L’attribut C++ qui n’est pas **extensible** a les mêmes fonctionnalités que l’attribut MIDL qui n’est pas [extensible](/windows/win32/Midl/nonextensible) .

L’utilisation de la **préextensibilité** requiert également l’attribut [oleautomation](oleautomation.md) .

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de l’attribut **unextensible** :

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|`dual` et `oleautomation` , ou `dispinterface`|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
