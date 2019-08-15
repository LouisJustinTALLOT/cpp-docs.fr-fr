---
title: unextensible (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514398"
---
# <a name="nonextensible"></a>nonextensible

Spécifie que `IDispatch` l’implémentation de comprend uniquement les propriétés et les méthodes listées dans la description de l’interface et ne peut pas être étendue avec des membres supplémentaires au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Notes

L' C++ attribut unextensible a les mêmes fonctionnalités que l’attribut MIDL qui n’est pas [extensible](/windows/win32/Midl/nonextensible) .

L’utilisation de la préextensibilité requiert également l’attribut [oleautomation](oleautomation.md) .

## <a name="example"></a>Exemples

Le code suivant illustre une utilisation de l' attribut unextensible:

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|`dual`et `oleautomation`, ou`dispinterface`|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)