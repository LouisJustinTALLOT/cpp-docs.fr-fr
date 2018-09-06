---
title: Macros d’état de l’objet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04bad7c90869eb5a5b87a465b175e4ed3f0b9991
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751509"
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

*MiscStatus*  
Indicateurs OLEMISC tout applicables.

### <a name="remarks"></a>Notes

Cette macro est utilisée pour définir les indicateurs OLEMISC pour un contrôle ActiveX. Reportez-vous à [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) pour plus d’informations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
