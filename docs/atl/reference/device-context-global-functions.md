---
description: 'En savoir plus sur : fonctions globales du contexte de périphérique'
title: Fonctions globales du contexte de périphérique
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: f5e87271170e29a2f0cc4d42b4e7739a5fd869ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139904"
---
# <a name="device-context-global-functions"></a>Fonctions globales du contexte de périphérique

Cette fonction crée un contexte de périphérique pour un appareil donné.

|Nom|Description|
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crée un contexte de périphérique.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a> AtlCreateTargetDC

Crée un contexte de périphérique pour l’appareil spécifié dans la structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) .

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Paramètres

*HDC*<br/>
dans Handle existant d’un contexte de périphérique (ou NULL).

*PTD*<br/>
dans Pointeur vers la `DVTARGETDEVICE` structure qui contient des informations sur l’appareil cible.

### <a name="return-value"></a>Valeur renvoyée

Retourne le handle vers un contexte de périphérique pour l’appareil spécifié dans le `DVTARGETDEVICE` . Si aucun appareil n’est spécifié, retourne le descripteur au périphérique d’affichage par défaut.

### <a name="remarks"></a>Notes

Si la structure est NULL et que *HDC* a la valeur null, crée un contexte de périphérique pour le périphérique d’affichage par défaut.

Si *HDC* n’a pas la valeur null et que *PTD* a la valeur null, la fonction retourne le *HDC* existant.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
