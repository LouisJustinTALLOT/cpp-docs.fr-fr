---
title: agrégats (C++ COM attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregates
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
ms.openlocfilehash: 12e6af31c2714095cf2ecf51e4f067081789a9e0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028696"
---
# <a name="aggregates"></a>agrégats

Indique que l’objet agrège l’objet spécifié par le CLSID.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregates(clsid, variable_name) ]
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
Spécifie le CLSID de l’objet qui peut être agrégé.

*nom_variable*<br/>
Nom de la variable à insérer. Cette variable contient le `IUnknown` de l’objet en cours d’agrégation.

## <a name="remarks"></a>Notes

Quand il est appliqué à un objet, l’attribut C++ **aggregates** implémente un wrapper externe pour l’objet en cours d’agrégation (spécifié par `clsid`).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliquée, `vi_progid` et `coclass` sont également appliquées.

### <a name="atl-projects"></a>Projets ATL

Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. Tout d’abord, l’entrée suivante est ajoutée au mappage COM de l’objet cible :

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)
```

Ensuite, la macro [DECLARE_GET_CONTROLLING_UNKNOWN](../../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) est également ajoutée.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_aggregates.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

// requires 'aggregatable.dll'
// see aggregatable attribute to create 'aggregatable.dll'
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;

[module (name="MYObject")];
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]
__interface IObject
{
};

[ coclass, aggregates(__uuidof(CMyClass)),
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]
struct CObject : IObject
{
   int i;
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Oui|
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agrégation](/windows/desktop/com/aggregation)<br/>
[Aggregatable](/windows/desktop/Midl/aggregatable)<br/>
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)