---
title: CriticalSection::Lock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f13af220107ba8d5bc5c26c65c2034f125a39454
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382451"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock, méthode

Attend que la propriété de l’objet de section critique spécifié. La fonction retourne quand le thread appelant est accordé à la propriété.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Un objet spécifié par l’utilisateur de section critique.

## <a name="return-value"></a>Valeur de retour

Un objet de verrouillage qui peut être utilisé pour déverrouiller la section critique en cours.

## <a name="remarks"></a>Notes

La première **verrou** fonction affecte l’objet en cours de la section critique. La seconde **verrou** fonction affecte une section critique spécifié par l’utilisateur.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[CriticalSection, classe](../windows/criticalsection-class.md)