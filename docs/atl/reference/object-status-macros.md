---
title: Macros d’état d’objet
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 9c4df80b2b9828077ec3738bc296f19aadf2df68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658950"
---
# <a name="object-status-macros"></a>Macros d’état d’objet

Cette macro définit des indicateurs qui appartiennent à des contrôles ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Utilisé dans les contrôles ActiveX ATL pour définir les indicateurs OLEMISC.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

Utilisé dans les contrôles ActiveX ATL pour définir les indicateurs OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Paramètres

*MiscStatus*<br/>
Indicateurs OLEMISC tout applicables.

### <a name="remarks"></a>Notes

Cette macro est utilisée pour définir les indicateurs OLEMISC pour un contrôle ActiveX. Reportez-vous à [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) pour plus d’informations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
