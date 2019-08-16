---
title: Fonctions globales du contexte de périphérique
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496102"
---
# <a name="device-context-global-functions"></a>Fonctions globales du contexte de périphérique

Cette fonction crée un contexte de périphérique pour un appareil donné.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crée un contexte de périphérique.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Crée un contexte de périphérique pour l’appareil spécifié dans la structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) .

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Paramètres

*hdc*<br/>
dans Handle existant d’un contexte de périphérique (ou NULL).

*ptd*<br/>
dans Pointeur vers la `DVTARGETDEVICE` structure qui contient des informations sur l’appareil cible.

### <a name="return-value"></a>Valeur de retour

Retourne le handle vers un contexte de périphérique pour l’appareil spécifié dans `DVTARGETDEVICE`le. Si aucun appareil n’est spécifié, retourne le descripteur au périphérique d’affichage par défaut.

### <a name="remarks"></a>Notes

Si la structure est NULL et que *HDC* a la valeur null, crée un contexte de périphérique pour le périphérique d’affichage par défaut.

Si *HDC* n’a pas la valeur null et que *PTD* a la valeur null, la fonction retourne le *HDC*existant.

## <a name="requirements"></a>Configuration requise

**En-tête:** atlwin. h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
