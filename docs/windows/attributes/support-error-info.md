---
title: support_error_info (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c6bb07071efa162b5b33ae5f1dfe72ac7ea02e8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790668"
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

L’attribut C++ **support_error_info** implémente la prise en charge permettant de retourner au client les erreurs détaillées et contextuelles rencontrées par l’objet cible. Pour l’objet prendre en charge les erreurs, les méthodes de la `IErrorInfo` interface doit être implémentée par l’objet. Pour plus d’informations, consultez [prise en charge d’IDispatch et IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Cet attribut ajoute la [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) classe comme classe de base à l’objet cible. Il en résulte une implémentation par défaut de `ISupportErrorInfo` et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet.

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

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)  