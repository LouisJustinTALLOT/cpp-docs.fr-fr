---
description: 'En savoir plus sur : fonctions globales de gestion des événements'
title: Fonctions globales de gestion des événements
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: 89e5ec38ff8884f5b99592541df6e397e2dd7116
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139852"
---
# <a name="event-handling-global-functions"></a>Fonctions globales de gestion des événements

Cette fonction fournit un gestionnaire d’événements.

> [!IMPORTANT]
> La fonction indiquée dans le tableau suivant ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

|Nom|Description|
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Attend qu’un objet soit signalé, en attendant la distribution des messages de fenêtre en fonction des besoins.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a> AtlWaitWithMessageLoop

Attend que l'objet soit signalé tout en distribuant les messages de fenêtre en fonction des besoins.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Paramètres

*hEvent*<br/>
dans Handle de l’objet à attendre.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’objet a été signalé.

### <a name="remarks"></a>Notes

Cela est utile si vous souhaitez attendre que l’événement d’un objet se produise et en être informé, mais autoriser la distribution des messages de fenêtre en attente.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
