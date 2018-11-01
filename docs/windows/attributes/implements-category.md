---
title: implements_category (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: a63504ce327bc2f1996c74dba9c51dc345e15abd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647159"
---
# <a name="implementscategory"></a>implements_category

Spécifie les catégories de composant implémentés par la classe cible.

## <a name="syntax"></a>Syntaxe

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Paramètres

*implements_category*<br/>
L’ID de la catégorie implémentée.

## <a name="remarks"></a>Notes

Le **implements_category** attribut C++ Spécifie les catégories de composant implémentés par la classe cible. Pour cela, la création d’un mappage de catégorie et en ajoutant des entrées distinctes spécifiées par le **implements_category** attribut. Pour plus d’informations, consultez [quelles sont les catégories de composants et comment faire leur travail ?](https://msdn.microsoft.com/library/windows/desktop/ms694322).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliquée, `vi_progid` et `coclass` sont également appliquées.

## <a name="example"></a>Exemple

Le code suivant spécifie que l’objet suivant implémente la `Control` catégorie.

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
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Oui|
|**Attributs requis**|Une des opérations suivantes : `coclass`, `progid`, ou `vi_progid`|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)