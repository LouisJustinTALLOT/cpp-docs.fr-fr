---
title: Fonctions globales de gestion des événements
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: 02066f2e6cd215fdb68fcdb594307b646ee69cad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660393"
---
# <a name="event-handling-global-functions"></a>Fonctions globales de gestion des événements

Cette fonction fournit un gestionnaire d’événements.

> [!IMPORTANT]
>  La fonction répertoriée dans le tableau suivant ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Attend un objet soit signalé, en attendant la distribution des messages de fenêtre en fonction des besoins.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop

Attend que l'objet soit signalé tout en distribuant les messages de fenêtre en fonction des besoins.

> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Paramètres

*hEvent*<br/>
[in] Le handle de l’objet à attendre.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’objet a été signalé.

### <a name="remarks"></a>Notes

Cela est utile si vous voulez attendre un événement d’un objet à se produire et d’en être informé qui se produisent, mais autoriser les messages de fenêtre à être distribués durant l’attente.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
