---
title: registration_script (C++ attribut COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 0b2c4d576a699dea7772821b5635944b2663c57c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024372"
---
# <a name="registrationscript"></a>registration_script

Exécute le script d’inscription personnalisé spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Paramètres

*script*<br/>
Le chemin d’accès complet à un fichier de script (d’inscription.rgs) d’inscription personnalisé. La valeur **aucun**, tel que `script = "none"`, indique ne qu’aucune exigence de l’inscription de la coclasse.

## <a name="remarks"></a>Notes

Le **registration_script** C++ attribut exécute le script d’inscription personnalisé spécifié par *script*. Si cet attribut n’est pas spécifié, un fichier .rgs standard (contenant des informations pour l’inscription du composant) est utilisé. Pour plus d’informations sur les fichiers .rgs, consultez [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément.

## <a name="example"></a>Exemple

Le code suivant spécifie que le composant a un script de Registre appelé cpp_attr_ref_registration_script.rgs.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[rdx](rdx.md)