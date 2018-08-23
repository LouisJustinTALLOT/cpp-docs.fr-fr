---
title: CriticalSection::TryLock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 382dbdd2d0816d6ab0846acd0f8c164cd542114f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575839"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock, méthode

Tentatives de saisie d’une section critique sans bloquer. Si l’appel réussit, le thread appelant prend possession de la section critique.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*cs*  
Un objet spécifié par l’utilisateur de section critique.

## <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la section critique est entrée avec succès ou le thread actif possède déjà la section critique. Zéro si un autre thread possède déjà la section critique.

## <a name="remarks"></a>Notes

La première **TryLock** fonction affecte l’objet en cours de la section critique. La seconde **TryLock** fonction affecte une section critique spécifié par l’utilisateur.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[CriticalSection, classe](../windows/criticalsection-class.md)