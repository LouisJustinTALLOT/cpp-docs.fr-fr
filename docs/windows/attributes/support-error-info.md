---
title: support_error_info (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: c05b6735c5c29e44f3cc190a150a5efe02025519
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023761"
---
# <a name="supporterrorinfo"></a>support_error_info

Implémente la prise en charge du retour d’erreurs détaillées.

## <a name="syntax"></a>Syntaxe

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Paramètres

*error_interface*<br/>
L’identificateur de l’interface qui implémente `IErrorInfo`.

## <a name="remarks"></a>Notes

L’attribut C++ **support_error_info** implémente la prise en charge permettant de retourner au client les erreurs détaillées et contextuelles rencontrées par l’objet cible. Pour l’objet prendre en charge les erreurs, les méthodes de la `IErrorInfo` interface doit être implémentée par l’objet. Pour plus d’informations, consultez [Prise en charge d’IDispatch et IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Cet attribut ajoute la classe [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) comme classe de base à l’objet cible. Il en résulte une implémentation par défaut de `ISupportErrorInfo` et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet.

## <a name="example"></a>Exemple

Le code suivant ajoute la prise en charge par défaut pour le `ISupportErrorInfo` interface pour le `CMyClass` objet.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**|
|**Renouvelable**|Oui|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)