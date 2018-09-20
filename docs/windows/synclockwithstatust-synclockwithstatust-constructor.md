---
title: Synclockwithstatust::synclockwithstatust, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 020632ff17ade10e7fcb9cd46d245849189b6860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416784"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT, constructeur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Une référence rvalue à un autre **SyncLockWithStatusT** objet.

*sync*<br/>
Une référence à un autre **SyncLockWithStatusT** objet.

*status*<br/>
La valeur de la [status_](../windows/synclockwithstatust-status-data-member.md) membre de données de la *autres* paramètre ou le *synchronisation* paramètre.

## <a name="remarks"></a>Notes

Initialise une nouvelle instance de la **SyncLockWithStatusT** classe.

Le premier constructeur initialise actuel **SyncLockWithStatusT** objet à partir d’un autre **SyncLockWithStatusT** spécifié par le paramètre *autres*, puis invalide l’autre **SyncLockWithStatusT** objet. Le deuxième constructeur est **protégé**et l’initialise actuel **SyncLockWithStatusT** objet à un état non valide.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[SyncLockWithStatusT, classe](../windows/synclockwithstatust-class.md)<br/>
[SyncLockWithStatusT::GetStatus, méthode](../windows/synclockwithstatust-getstatus-method.md)