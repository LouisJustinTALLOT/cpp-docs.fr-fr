---
description: 'En savoir plus sur : exécution du programme en tant que serveur local'
title: Exécution du programme en tant que serveur local
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: 1cdf3cef0773769318d68964b28bb60ca66666d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157489"
---
# <a name="running-the-program-as-a-local-server"></a>Exécution du programme en tant que serveur local

Si l’exécution du programme en tant que service est peu commode, vous pouvez modifier temporairement le registre afin que le programme soit exécuté en tant que serveur local normal. Renommez simplement la `LocalService` valeur sous votre AppID en `_LocalService` et assurez-vous que la `LocalServer32` clé sous votre CLSID est définie correctement. (Notez que l’utilisation de DCOMCNFG pour spécifier que votre application doit être exécutée sur un autre ordinateur renomme votre `LocalServer32` clé en `_LocalServer32` .) L’exécution de votre programme en tant que serveur local prend quelques secondes supplémentaires au démarrage, car l’appel à `StartServiceCtrlDispatcher` dans `CAtlServiceModuleT::Start` prend quelques secondes avant d’échouer.

## <a name="see-also"></a>Voir aussi

[Conseils de débogage](../atl/debugging-tips.md)
