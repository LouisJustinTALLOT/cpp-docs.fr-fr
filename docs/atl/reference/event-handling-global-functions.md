---
title: Event Handling Global Functions
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330132"
---
# <a name="event-handling-global-functions"></a>Event Handling Global Functions

Cette fonction fournit un gestionnaire d’événements.

> [!IMPORTANT]
> La fonction indiquée dans le tableau suivant ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Attend qu’un objet soit signalé, en attendant l’envoi de messages de fenêtre au besoin.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop

Attend que l'objet soit signalé tout en distribuant les messages de fenêtre en fonction des besoins.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Paramètres

*hEvent*<br/>
[dans] La poignée de l’objet à attendre.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’objet a été signalé.

### <a name="remarks"></a>Notes

Ceci est utile si vous voulez attendre que l’événement d’un objet se produise et être informé de ce qui se passe, mais permettre aux messages de fenêtre d’être expédiés en attendant.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
