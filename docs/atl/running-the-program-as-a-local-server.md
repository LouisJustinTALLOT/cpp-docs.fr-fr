---
title: Le programme en cours d’exécution en tant qu’un serveur Local | Documents Microsoft
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
ms.openlocfilehash: c2b8a79978528493e02ac5a272dafe8da6fdc1d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360441"
---
# <a name="running-the-program-as-a-local-server"></a>Le programme en cours d’exécution en tant qu’un serveur Local
Si le programme en cours d’exécution en tant que service n’est pas pratique, vous pouvez modifier temporairement le Registre afin que le programme est exécuté en tant qu’un fonctionnement normal du serveur local. Renommer simplement le `LocalService` valeur sous votre AppID à `_LocalService` et assurez-vous que le `LocalServer32` clé sous votre CLSID est définie correctement. (Notez que, à l’aide de DCOMCNFG pour spécifier que votre application doit être exécutée sur un ordinateur différent renomme votre `LocalServer32` clé à `_LocalServer32`.) Exécuter votre programme, comme un serveur local prend quelques secondes supplémentaires au démarrage, car l’appel à **StartServiceCtrlDispatcher** dans `CAtlServiceModuleT::Start` prend quelques secondes avant d’échouer.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de débogage](../atl/debugging-tips.md)

