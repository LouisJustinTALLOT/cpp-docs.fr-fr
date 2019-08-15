---
title: implements_category (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: 6e0036b7008b67a1e21bcbe64977f4703bbdf3be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514632"
---
# <a name="implements_category"></a>implements_category

Spécifie les catégories de composants implémentées par la classe cible.

## <a name="syntax"></a>Syntaxe

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Paramètres

*implements_category*<br/>
ID de la catégorie implémentée.

## <a name="remarks"></a>Notes

L’attribut **implements_category** C++ spécifie les catégories de composants implémentées par la classe cible. Pour ce faire, créez une carte de catégorie et ajoutez des entrées distinctes spécifiées par l’attribut **implements_category** . Pour plus d’informations, consultez [catégories de composants et fonctionnement](/windows/win32/com/component-categories-and-how-they-work).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliqué, `vi_progid` et `coclass` sont également appliqués.

## <a name="example"></a>Exemples

Le code suivant spécifie que l’objet suivant implémente `Control` la catégorie.

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Oui|
|**Attributs requis**|L’une des valeurs suivantes `coclass`: `progid`, ou`vi_progid`|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)