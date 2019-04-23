---
title: nonextensible (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: ed396b3d55e16cf195949c713ab574812b796a1a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032074"
---
# <a name="nonextensible"></a>nonextensible

Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peut pas être étendus avec des membres supplémentaires en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Notes

Le **nonextensible** attribut C++ a les mêmes fonctionnalités que le [nonextensible](/windows/desktop/Midl/nonextensible) attribut MIDL.

Utilisation de **nonextensible** requiert également le [oleautomation](oleautomation.md) attribut.

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de la **nonextensible** attribut :

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
|**Attributs requis**|`dual` et `oleautomation`, ou `dispinterface`|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)