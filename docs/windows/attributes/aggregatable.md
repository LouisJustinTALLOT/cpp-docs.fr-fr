---
description: 'En savoir plus sur : agrégeables'
title: agrégeables (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 0ba6c96f1b12deb2db91c20f0558961ef1ed6f61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314254"
---
# <a name="aggregatable"></a>aggregatable

Indique que la classe prend en charge l’agrégation.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Facultatif Paramètre pour indiquer quand l’objet COM peut être agrégé :

- `never` L’objet COM ne peut pas être agrégé.

- `allowed` L’objet COM peut être créé directement ou peut être agrégé. Il s’agit de la valeur par défaut.

- `always` L’objet COM ne peut pas être créé directement et peut uniquement être agrégé. Lorsque vous appelez `CoCreateInstance` pour cet objet, vous devez spécifier l’interface de l’objet d’agrégation `IUnknown` (le contrôle `IUnknown` ).

## <a name="remarks"></a>Notes

L’attribut C++ pouvant être **agrégé** a les mêmes fonctionnalités que l’attribut MIDL [agrégé](/windows/win32/Midl/aggregatable) . Cela signifie que le compilateur passera l’attribut pouvant être **agrégé** par le biais du fichier. idl généré.

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliqué, `vi_progid` et `coclass` sont également appliqués.

### <a name="atl-projects"></a>Projets ATL

Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit précédemment, l’attribut ajoute également l’une des macros suivantes à la classe cible :

|Valeur du paramètre|Macro insérée|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Renouvelable**|Non|
|**Attributs requis**|Une ou plusieurs des valeurs suivantes : `coclass` , `progid` ou `vi_progid` .|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agrégation](/windows/win32/com/aggregation)
