---
title: Fonctions globales contextuelles de l’appareil
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330152"
---
# <a name="device-context-global-functions"></a>Fonctions globales contextuelles de l’appareil

Cette fonction crée un contexte d’appareil pour un appareil donné.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crée un contexte d’appareil.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Crée un contexte d’appareil pour l’appareil spécifié dans la structure [DVTARGETDEVICE.](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Paramètres

*Hdc*<br/>
[dans] La poignée existante d’un contexte d’appareil, ou NULL.

*Ptd*<br/>
[dans] Un pointeur `DVTARGETDEVICE` vers la structure qui contient des informations sur l’appareil cible.

### <a name="return-value"></a>Valeur de retour

Retourne la poignée dans un contexte d’appareil pour l’appareil spécifié dans le `DVTARGETDEVICE`. Si aucun appareil n’est spécifié, renvoie la poignée à l’appareil d’affichage par défaut.

### <a name="remarks"></a>Notes

Si la structure est NULL et *hdc* est NULL, crée un contexte d’appareil pour le périphérique d’affichage par défaut.

Si *hdc n’est* pas NULL et *ptd* est NULL, la fonction renvoie le *hdc*existant .

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
