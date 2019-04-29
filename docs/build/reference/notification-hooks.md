---
title: Raccordements de notification
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 884d8e8479b7cad28d99e19adfac4d05dbeec5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320472"
---
# <a name="notification-hooks"></a>Raccordements de notification

Les raccordements de notification sont appelés juste avant que les actions suivantes sont exécutées dans la routine d’assistance :

- Le descripteur stocké de la bibliothèque est vérifié pour voir s’il a déjà été chargé.

- **LoadLibrary** est appelé pour tenter de la charge de la DLL.

- **GetProcAddress** est appelé pour tenter d’obtenir l’adresse de la procédure.

- Revenez au thunk de chargement différé.

Le raccordement de notification est activé :

- En fournissant une nouvelle définition du pointeur **__pfnDliNotifyHook2** qui est initialisé pour pointer vers votre propre fonction qui reçoit les notifications.

   \- ou -

- En définissant le pointeur **__pfnDliNotifyHook2** à votre fonction de raccordement avant tout appel à la DLL que le programme est différer le chargement.

Si la notification est **dliStartProcessing**, la fonction de raccordement peut retourner :

- NULL

   L’assistance par défaut gère le chargement de la DLL. Cela est utile pour être appelée uniquement à titre d’information.

- pointeur de fonction

   Ignorer la gestion du chargement différé par défaut. Cela vous permet de fournir votre propre gestionnaire de charge.

Si la notification est **dliNotePreLoadLibrary**, la fonction de raccordement peut retourner :

- 0, s’il souhaite simplement des notifications d’information.

- HMODULE pour la DLL chargée, s’il chargé la DLL proprement dite.

Si la notification est **dliNotePreGetProcAddress**, la fonction de raccordement peut retourner :

- 0, s’il souhaite simplement des notifications d’information.

- Adresse de la fonction importée, si la fonction de raccordement Obtient l’adresse elle-même.

Si la notification est **dliNoteEndProcessing**, valeur de retour de la fonction de raccordement est ignorée.

Si ce pointeur est initialisé (différent de zéro), l’assistance de chargement différé appelle la fonction à certains points de notification tout au long de son exécution. Le pointeur de fonction a la définition suivante :

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

Les notifications passent dans un **DelayLoadInfo** structure à la fonction de raccordement, ainsi que la valeur de notification. Ces données sont identiques à celle utilisée par la routine d’assistance de chargement différé. La valeur de la notification sera une des valeurs définies dans [définitions des structures et constantes](structure-and-constant-definitions.md).

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](error-handling-and-notification.md)
