---
title: CAtlServiceModuleT::ServiceMain, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs:
- C++
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9dff3fa3f3ed20406955570f2ad72531f4e44f11
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848119"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain, fonction
Appelle le Gestionnaire de contrôle des services (SCM) `ServiceMain` lorsque vous ouvrez l’application Services du panneau, sélectionnez le service, puis cliquez sur **Démarrer**.  
  
 Une fois le GCL appelle `ServiceMain`, un service doit donner au SCM une fonction gestionnaire. Cette fonction vous permet du GCL obtenir l’état du service et passer des instructions spécifiques (par exemple, la suspension ou l’arrêt). Le SCM obtient cette fonction lorsque le service passe `_Handler` à la fonction API Win32, [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (`_Handler` est une fonction membre statique qui appelle la fonction membre non statique [gestionnaire](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Au démarrage, un service doit également informer le SCM de son état actuel. Pour cela, en passant SERVICE_START_PENDING à la fonction API Win32, il [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` appelle ensuite `CAtlExeModuleT::InitializeCom`, qui appelle la fonction API Win32 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Par défaut, `InitializeCom` passe l’indicateur COINIT_MULTITHREADED à la fonction. Cet indicateur indique que le programme doit être un serveur libre de threads.  
  
 Maintenant, `CAtlServiceModuleT::Run` est appelée pour effectuer le travail principal du service. `Run` continue à s’exécuter jusqu'à ce que le service est arrêté.  
  
## <a name="see-also"></a>Voir aussi  
 [Services](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

