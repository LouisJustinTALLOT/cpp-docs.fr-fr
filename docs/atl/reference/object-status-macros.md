---
title: Macros d’état d’objet
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326178"
---
# <a name="object-status-macros"></a>Macros d’état d’objet

Cette macro fixe des drapeaux appartenant aux commandes ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Utilisé dans les commandes ATL ActiveX pour définir les drapeaux OLEMISC.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Utilisé dans les commandes ATL ActiveX pour définir les drapeaux OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Paramètres

*miscstatus*<br/>
Tous les drapeaux OLEMISC applicables.

### <a name="remarks"></a>Notes

Cette macro est utilisée pour définir les drapeaux OLEMISC pour un contrôle ActiveX. Référez-vous à [IOleObject:GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) pour plus de détails.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
