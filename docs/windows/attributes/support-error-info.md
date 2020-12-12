---
description: 'En savoir plus sur : support_error_info'
title: support_error_info (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: 3d707179511dadda0f24a2d13e95a32de3705f62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327279"
---
# <a name="support_error_info"></a>support_error_info

Implémente la prise en charge du retour d’erreurs détaillées.

## <a name="syntax"></a>Syntaxe

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Paramètres

*error_interface*<br/>
Identificateur de l’interface qui implémente `IErrorInfo` .

## <a name="remarks"></a>Notes

L’attribut C++ **support_error_info** implémente la prise en charge permettant de retourner au client les erreurs détaillées et contextuelles rencontrées par l’objet cible. Pour que l’objet prenne en charge les erreurs, les méthodes de l' `IErrorInfo` interface doivent être implémentées par l’objet. Pour plus d’informations, consultez [Prise en charge d’IDispatch et IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Cet attribut ajoute la classe [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) comme classe de base à l’objet cible. Il en résulte une implémentation par défaut de `ISupportErrorInfo` et peut être utilisée quand une seule interface génère des erreurs sur un objet.

## <a name="example"></a>Exemple

Le code suivant ajoute la prise en charge par défaut de l' `ISupportErrorInfo` interface à l' `CMyClass` objet.

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**|
|**Renouvelable**|Oui|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
