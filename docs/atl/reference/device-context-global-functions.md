---
title: Fonctions globales de contexte de périphérique
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: 25ceae897d3cc845ab06fd4d898c87518b15eacb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551201"
---
# <a name="device-context-global-functions"></a>Fonctions globales de contexte de périphérique

Cette fonction crée un contexte de périphérique pour un appareil donné.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crée un contexte de périphérique.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Crée un contexte de périphérique pour le périphérique spécifié dans le [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) structure.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Paramètres

*HDC*<br/>
[in] Le handle existant d’un contexte de périphérique, ou NULL.

*ptd*<br/>
[in] Un pointeur vers le `DVTARGETDEVICE` structure qui contient des informations sur l’appareil cible.

### <a name="return-value"></a>Valeur de retour

Retourne le handle vers un contexte de périphérique pour le périphérique spécifié dans le `DVTARGETDEVICE`. Si aucun périphérique n’est spécifié, retourne le handle vers le périphérique d’affichage par défaut.

### <a name="remarks"></a>Notes

Si la structure est NULL et *hdc* est NULL, crée un contexte de périphérique pour le périphérique d’affichage par défaut.

Si *hdc* n’est pas NULL et *ptd* est NULL, la fonction retourne existant *hdc*.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
