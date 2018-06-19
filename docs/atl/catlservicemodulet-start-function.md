---
title: Fonction CAtlServiceModuleT::Start | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da8d7358c634416941a551c93c6a2772549a3fd2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357275"
---
# <a name="catlservicemoduletstart-function"></a>Fonction CAtlServiceModuleT::Start
Lorsque le service est exécuté, **_tWinMain** appelle **CAtlServiceModuleT::WinMain**, qui à son tour appelle `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` définit un tableau de **SERVICE_TABLE_ENTRY** structures qui mappe chaque service à sa fonction de démarrage. Ce tableau est ensuite transmis à la fonction API Win32, [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). En théorie, un EXE pourrait traiter plusieurs services et le tableau peut avoir plusieurs **SERVICE_TABLE_ENTRY** structures. Actuellement, toutefois, un service généré ATL prend en charge qu’un seul service par EXE. Par conséquent, le tableau a une seule entrée qui contient le nom du service et **_ServiceMain** en tant que la fonction de démarrage. **_ServiceMain** est une fonction membre statique de `CAtlServiceModuleT` qui appelle la fonction membre non statique, `ServiceMain`.  
  
> [!NOTE]
>  Échec de **StartServiceCtrlDispatcher** pour se connecter à la commande de service manager (SCM) signifie probablement que le programme n’est pas en cours d’exécution en tant que service. Dans ce cas, le programme appelle `CAtlServiceModuleT::Run` directement afin que le programme peut s’exécuter comme un serveur local. Pour plus d’informations sur l’exécution du programme en tant qu’un serveur local, consultez [conseils de débogage](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

