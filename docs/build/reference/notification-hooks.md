---
description: 'En savoir plus sur : raccordements de notification'
title: Raccordements de notification
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 716d2b31faa71c77ec436662ce00368d15afc4b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209748"
---
# <a name="notification-hooks"></a>Raccordements de notification

Les raccordements de notification sont appelés juste avant que les actions suivantes soient effectuées dans la routine d’assistance :

- Le descripteur stocké de la bibliothèque est vérifié pour voir s’il a déjà été chargé.

- **LoadLibrary** est appelé pour tenter le chargement de la dll.

- **GetProcAddress** est appelé pour tenter d’accéder à l’adresse de la procédure.

- Revenez au thunk de chargement d’importation différé.

Le raccordement de notification est activé :

- En fournissant une nouvelle définition du pointeur **__pfnDliNotifyHook2** qui est initialisée pour pointer vers votre propre fonction qui reçoit les notifications.

   \- ou -

- En définissant le pointeur **__pfnDliNotifyHook2** à votre fonction de raccordement avant tout appel à la dll que le programme charge en différé.

Si la notification est **dliStartProcessing**, la fonction de raccordement peut retourner :

- NULL

   Le programme d’assistance par défaut gère le chargement de la DLL. Cela est utile pour être appelé à titre d’information uniquement.

- pointeur de fonction

   Contourner la gestion du chargement différé par défaut. Cela vous permet de fournir votre propre gestionnaire de charge.

Si la notification est **dliNotePreLoadLibrary**, la fonction de raccordement peut retourner :

- 0, si elle souhaite simplement recevoir des notifications d’information.

- HMODULE pour la DLL chargée, si elle a chargé la DLL elle-même.

Si la notification est **dliNotePreGetProcAddress**, la fonction de raccordement peut retourner :

- 0, si elle souhaite simplement recevoir des notifications d’information.

- Adresse de la fonction importée, si la fonction de raccordement obtient l’adresse elle-même.

Si la notification est **dliNoteEndProcessing**, la valeur de retour de la fonction de raccordement est ignorée.

Si ce pointeur est initialisé (différent de zéro), le programme d’assistance de chargement différé appellera la fonction à certains points de notification tout au long de son exécution. Le pointeur de fonction a la définition suivante :

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

Les notifications passent dans une structure **DelayLoadInfo** à la fonction de raccordement et à la valeur de notification. Ces données sont identiques à celles utilisées par la routine d’assistance de chargement différé. La valeur de notification sera l’une des valeurs définies dans les [définitions de structure et de constante](structure-and-constant-definitions.md).

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](error-handling-and-notification.md)
