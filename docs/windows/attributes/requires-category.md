---
title: requires_category (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: d566e74a9019259e526fa27aec26500e9ef3e1c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846002"
---
# <a name="requires_category"></a>requires_category

Spécifie les catégories de composants nécessaires de la classe cible.

## <a name="syntax"></a>Syntaxe

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Paramètres

*requires_category*<br/>
ID de la catégorie requise.

## <a name="remarks"></a>Notes

L’attribut **requires_category** C++ spécifie les catégories de composants requises par la classe cible. Pour plus d’informations, consultez [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément.

## <a name="example"></a>Exemple

Le code suivant requiert que l’objet implémente la catégorie de contrôle.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|Une ou plusieurs des valeurs suivantes : `coclass` , `progid` ou `vi_progid` .|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[implements_category](implements-category.md)
