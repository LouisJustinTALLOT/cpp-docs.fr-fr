---
description: 'En savoir plus sur : registration_script'
title: registration_script (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 3722a799818c8ad76d710e4c570bc5fdd6b2e10c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327346"
---
# <a name="registration_script"></a>registration_script

Exécute le script d’inscription personnalisé spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Paramètres

*script*<br/>
Chemin d’accès complet à un fichier de script d’inscription personnalisé (. RGS). La valeur **None**, par exemple `script = "none"` , indique que la coclasse n’a pas de spécifications d’inscription.

## <a name="remarks"></a>Notes

L’attribut **registration_script** C++ exécute le script d’inscription personnalisé spécifié par le *script*. Si cet attribut n’est pas spécifié, un fichier. RGS standard (contenant les informations d’inscription du composant) est utilisé. Pour plus d’informations sur les fichiers. RGS, consultez [le composant Registre ATL (Registrar)](../../atl/atl-registry-component-registrar.md).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément.

## <a name="example"></a>Exemple

Le code suivant spécifie que le composant a un script de Registre appelé cpp_attr_ref_registration_script. RGS.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
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

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[rdx](rdx.md)
