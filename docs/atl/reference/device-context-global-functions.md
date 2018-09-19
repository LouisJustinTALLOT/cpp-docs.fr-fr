---
title: Fonctions globales de contexte de périphérique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac2e56e4b13f739f61df5b37ab70689784a39882
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077540"
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
