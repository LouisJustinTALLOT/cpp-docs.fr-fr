---
title: Le programme en cours d’exécution en tant qu’un serveur Local | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2e44ba51a878d293ad5b497a1638cc9d7dc76
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848481"
---
# <a name="running-the-program-as-a-local-server"></a>Le programme en cours d’exécution en tant qu’un serveur Local
Si le programme en cours d’exécution en tant que service n’est pas pratique, vous pouvez modifier temporairement le Registre afin que le programme est exécuté comme un serveur local normal. Renommer simplement le `LocalService` valeur sous votre AppID à `_LocalService` et vérifiez que le `LocalServer32` clé sous votre CLSID est définie correctement. (Notez qu’à l’aide de DCOMCNFG pour spécifier que votre application doit être exécutée sur un ordinateur différent renomme votre `LocalServer32` clé à `_LocalServer32`.) Votre programme en cours d’exécution comme un serveur local prend quelques secondes supplémentaires au démarrage, car l’appel à `StartServiceCtrlDispatcher` dans `CAtlServiceModuleT::Start` prend quelques secondes avant d’échouer.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de débogage](../atl/debugging-tips.md)

