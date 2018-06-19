---
title: Raccordements de notification | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0210c4ee058694594893a029789442c89003da2e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377817"
---
# <a name="notification-hooks"></a>Raccordements de notification
Les raccordements de notification sont appelés juste avant que les actions suivantes sont exécutées dans la routine d’assistance :  
  
-   Le descripteur stocké de la bibliothèque est vérifié pour voir s’il a déjà été chargé.  
  
-   **LoadLibrary** est appelé pour tenter le chargement de la DLL.  
  
-   **GetProcAddress** est appelé pour tenter d’obtenir l’adresse de la procédure.  
  
-   Revenir à un thunk de chargement différé.  
  
 Le raccordement de notification est activé :  
  
-   En fournissant une nouvelle définition du pointeur **__pfnDliNotifyHook2** qui est initialisé pour pointer vers votre propre fonction qui reçoit les notifications.  
  
     - ou -  
  
-   En définissant le pointeur **__pfnDliNotifyHook2** à votre fonction de raccordement avant tout appel à la DLL que le programme de différer le chargement.  
  
 Si la notification est **dliStartProcessing**, la fonction de raccordement peut retourner :  
  
 NULL  
 L’assistance par défaut gère le chargement de la DLL. Cela est utile pour être appelée uniquement à titre d’information.  
  
 pointeur de fonction  
 Ignorer la gestion de chargement différé par défaut. Cela vous permet de fournir votre propre gestionnaire de charge.  
  
 Si la notification est **dliNotePreLoadLibrary**, la fonction de raccordement peut retourner :  
  
-   0, s’il veut simplement des notifications d’information.  
  
-   Le HMODULE pour la DLL chargée, s’il chargé la DLL elle-même.  
  
 Si la notification est **dliNotePreGetProcAddress**, la fonction de raccordement peut retourner :  
  
-   0, s’il veut simplement des notifications d’information.  
  
-   Adresse de la fonction importée, si la fonction de raccordement Obtient l’adresse elle-même.  
  
 Si la notification est **dliNoteEndProcessing**, valeur de retour de la fonction de raccordement est ignorée.  
  
 Si ce pointeur est initialisé (différent de zéro), l’assistance de chargement différé appelle la fonction à certains points de notification tout au long de son exécution. Le pointeur de fonction a la définition suivante :  
  
```  
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
  
 Les notifications passent dans une **DelayLoadInfo** structure à la fonction de raccordement avec la valeur de notification. Ces données sont identiques à celle utilisée par la routine d’assistance de chargement différé. La valeur de la notification à une des valeurs définies dans [définitions des structures et constantes](../../build/reference/structure-and-constant-definitions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion et notification des erreurs](../../build/reference/error-handling-and-notification.md)