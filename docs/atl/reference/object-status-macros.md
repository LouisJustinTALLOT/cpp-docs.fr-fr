---
title: Macros d’état des objets
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: d9e2223739dc3d0636337e2e2f713c80dff50131
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835231"
---
# <a name="object-status-macros"></a>Macros d’état des objets

Cette macro définit les indicateurs appartenant aux contrôles ActiveX.

|Nom|Description|
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Utilisé dans les contrôles ActiveX ATL pour définir les indicateurs OLEMISC.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a> DECLARE_OLEMISC_STATUS

Utilisé dans les contrôles ActiveX ATL pour définir les indicateurs OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Paramètres

*miscstatus*<br/>
Tous les indicateurs OLEMISC applicables.

### <a name="remarks"></a>Notes

Cette macro est utilisée pour définir les indicateurs OLEMISC pour un contrôle ActiveX. Pour plus d’informations, reportez-vous à [IOleObject :: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
